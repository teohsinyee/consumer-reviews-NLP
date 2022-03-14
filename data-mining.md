# How to Scrape Google Play Reviews in 4 simple steps using Python

### 1. Download and Install Google Play Scraper Package <br>
```from google_play_scraper import app
    import pandas as pd
    import numpy as np
```

### 2. Find the App Id in Google Play Store
https://play.google.com/store/apps/details?id=my.gov.onegovappstore.mysejahtera
<br> The App Id for MySejahtera is `my.gov.onegovappstore.mysejahtera`

### 3. Scrape the Reviews <br>
- You can specify the country and language. <br>
- You can download reviews in different languages using [ISO-Code(Alpha-2)](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for language. <br>

```
#US Market

from google_play_scraper import Sort, reviews_all

us_reviews = reviews_all(
    'com.busuu.android.en',
    sleep_milliseconds=0, # defaults to 0
    lang='en', # defaults to 'en'
    country='us', # defaults to 'us'
    sort=Sort.NEWEST, # defaults to Sort.MOST_RELEVANT
)
```

### 4. Put the Reviews into Pandas DataFrame
```
df_busu = pd.DataFrame(np.array(us_reviews),columns=['review'])

df_busu = df_busu.join(pd.DataFrame(df_busu.pop('review').tolist()))

df_busu.head()
```
Reference: https://www.linkedin.com/pulse/how-scrape-google-play-reviews-4-simple-steps-using-python-kundi
