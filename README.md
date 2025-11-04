# 🎧 AWS Spotify Data Engineering Pipeline

## 🎯 Objective
Developed a cloud-based ETL pipeline to analyze Spotify streaming data and deliver **actionable insights** into user behavior, artist trends, and performance KPIs.

---

## 🧠 Business Impact
✅ Enabled real-time trend analysis and dynamic dashboards  
✅ Supported data-driven content & marketing decisions  
✅ Insights projected a **15% increase in regional engagement** and reduced churn via targeted playlists  

---

## ⚙️ Tech Stack
| Component | Technology |
|-----------|------------|
| Cloud Storage | AWS S3 |
| Database | AWS RDS (MySQL) |
| Processing | Python (Pandas, NumPy), SQL |
| BI Tools | AWS QuickSight, Tableau |
| Data Source | Spotify API |

---

## 📊 Pipeline Process Overview

### ✅ 1. **Data Extraction & Storage**
- Pulled streaming metadata from Spotify API  
- Stored raw data in **AWS S3** as the landing zone

### ✅ 2. **Transformation**
- Cleaned and normalized data using **Python ETL scripts**  
- Generated structured tables for relational modeling

### ✅ 3. **Data Modeling**
- Loaded clean data into **AWS RDS**  
- Built relational schema for efficient SQL querying

### ✅ 4. **Visualization**
- Built dashboards in **QuickSight** and **Tableau** for KPI reporting:
  - Stream counts
  - Churn rate
  - User engagement by region & time

---

## ✅ Architecture Diagram
(Stored in `/Architecture Diagram/`)


---

## 🧩 Sample Code Snippets

### ✅ Python: Extracting Data from Spotify API
```python
import spotipy
from spotipy.oauth2 import SpotifyClientCredentials
import pandas as pd

sp = spotipy.Spotify(auth_manager=SpotifyClientCredentials())

result = sp.search(q='genre:pop', type='track', limit=50)

tracks = []
for item in result['tracks']['items']:
    track_name = item['name']
    artist = item['artists'][0]['name']
    popularity = item['popularity']
    release_date = item['album']['release_date']
    tracks.append([track_name, artist, popularity, release_date])

df = pd.DataFrame(tracks, columns=['Track', 'Artist', 'Popularity', 'Release_Date'])
df.to_csv("spotify_tracks.csv", index=False)


SELECT artist, COUNT(*) AS total_streams
FROM streams
GROUP BY artist
ORDER BY total_streams DESC
LIMIT 10;

AWS-Spotify-Data-Engineering-Pipeline/
│
├── src/
│   ├── extract_spotify_api.py          # Pulls data from Spotify API
│   ├── transform_cleaning.py           # Cleans & structures data
│   └── load_to_rds.sql                 # SQL script for loading into RDS
│
├── Architecture Diagram/
│   └── pipeline_diagram.png            # Visual pipeline representation
│
├── Future Enhancements/
│   └── enhancements.md                 # Scalability & next-phase ideas
│
├── AWS Spotify.pdf                     # Written documentation/report
└── README.md                           # Project overview
📁 Project Folder Structure
AWS-Spotify-Data-Engineering-Pipeline/
│
├── src/
│   ├── extract_spotify_api.py          # Pulls data from Spotify API
│   ├── transform_cleaning.py           # Cleans & structures data
│   └── load_to_rds.sql                 # SQL script for loading into RDS
│
├── Architecture Diagram/
│   └── pipeline_diagram.png            # Visual pipeline representation
│
├── Future Enhancements/
│   └── enhancements.md                 # Scalability & next-phase ideas
│
├── AWS Spotify.pdf                     # Written documentation/report
└── README.md                           # Project overview

🔍 Key Insights

Pop & Hip-Hop dominate global engagement

Usage peaks between 6–9 PM

Regionalized playlists recommended → could improve retention 10–15%

Year-over-year streaming increase driven by user-generated playlists

✅ Business Value Delivered
KPI	Insight
MAU	Identified seasonal growth & engagement trends
Churn	Found high-risk listener segments
Retention	Personalized content boosted playback hours

aws etl pipeline data-engineering python sql spotify-api quicksight tableau
