# Predicting Spotify Track Commercial Success using Random Forest

## 📌 Project Objective
The main goal of this project is to predict the commercial success (popularity) of songs on Spotify based on their measurable audio features. By leveraging machine learning, specifically a Random Forest classifier, this project aims to uncover the "Hit Profile" and determine if popularity is driven by technical track parameters rather than purely random factors.

## 📊 Dataset
The dataset used for this project contains Spotify tracks and their corresponding audio features. 
* **Source:** [[Kaggle - Spotify Tracks Dataset](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)

### Data Dictionary
* **Popularity:** A value from 0 to 100, where 100 is the most popular. Calculated by an algorithm based on total plays and how recent those plays are.
* **Duration_ms:** The track length in milliseconds.
* **Explicit:** Boolean indicating whether the track has explicit lyrics (true = yes; false = no or unknown).
* **Danceability:** Describes how suitable a track is for dancing (0.0 = least danceable, 1.0 = most danceable) based on tempo, rhythm stability, and beat strength.
* **Energy:** A perceptual measure from 0.0 to 1.0 representing intensity and activity. Energetic tracks feel fast, loud, and noisy.
* **Key:** The estimated overall key of the track based on standard Pitch Class notation. (-1 = no key detected).
* **Loudness:** The overall loudness of a track in decibels (dB), averaged across the entire track.
* **Mode:** Indicates the modality (major or minor) of a track. Major is represented by 1 and minor is 0.
* **Speechiness:** Detects the presence of spoken words. Values > 0.66 indicate tracks probably made entirely of spoken words; 0.33 - 0.66 indicate both music and speech (e.g., rap); < 0.33 most likely represents non-speech music.
* **Acousticness:** A confidence measure from 0.0 to 1.0 of whether the track is acoustic.
* **Instrumentalness:** Predicts whether a track contains no vocals. The closer to 1.0, the greater likelihood the track contains no vocal content.
* **Liveness:** Detects the presence of an audience. Values > 0.8 provide strong likelihood that the track is live.
* **Valence:** A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. High valence sounds more positive (happy, cheerful), while low valence sounds more negative (sad, depressed, angry).
* **Tempo:** The overall estimated tempo of a track in beats per minute (BPM).
* **Time_signature:** An estimated time signature ranging from 3 to 7 (e.g., indicating a 3/4 to 7/4 time signature).

## ⚙️ Methodology
1. **Target Variable Definition:** A threshold of 50 was set for the `popularity` variable. Tracks falling into the upper quartile (Top 25%) were classified as a 'Hit' (`Yes`), and the rest as `No`.
2. **Data Preprocessing:** Unnecessary columns were removed, and proper data types (factors) were assigned to categorical variables.
3. **Model Training:** The dataset was split into training (70%) and testing (30%) sets. A **Random Forest** model (200 trees) was trained using 5-fold Cross-Validation.

## 🚀 Results & Insights
The model achieved an **AUC (Area Under the ROC Curve) score of 0.8552**, indicating a high discriminative ability. The algorithm successfully identifies most popular tracks, confirming that commercial success is heavily tied to specific audio characteristics.

### 🏆 The "Hit" Profile
Based on the top 5 most influential parameters, a successful track typically features:
* **Lower Valence:** Tending to lean towards sadder or angrier tones rather than purely joyful ones.
* **Duration:** Approximately 3.5 minutes.
* **Loudness:** Just under -8 dB.
* **Acousticness:** Low probability of using acoustic instruments.
* **Tempo:** Around 121 BPM.

## 🛠️ Tools & Libraries
* **Language:** R
* **Libraries:** `caret`, `tidyverse`, `doParallel`, `rsample`, `vip`, `pROC`, `knitr`, `kableExtra`
