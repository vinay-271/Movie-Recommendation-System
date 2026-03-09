# 🎬 Content-Based Movie Recommender System

A Machine Learning-based Movie Recommendation System that suggests similar movies based on a user's choice. Built using Natural Language Processing (NLP) techniques and deployed as an interactive web application using **Streamlit**.

## 📝 Overview
This project is a **Content-Based Recommender System**. It uses movie metadata—such as genres, keywords, cast, crew (director), and plot overviews—to find and recommend movies that are similar to the one the user searches for. 

If you like a particular movie, the system calculates the mathematical similarity between that movie and all other movies in the database, returning the top 5 closest matches.

## ✨ Features
* **Intelligent Recommendations:** Uses Cosine Similarity to recommend the top 5 most similar movies.
* **NLP Preprocessing:** Utilizes text stemming (NLTK) and stop-word removal to optimize text data.
* **Tag Generation:** Combines Cast, Crew, Genres, Keywords, and Overview into custom tags for accurate predictions.
* **Interactive Web App:** A clean, user-friendly UI built with Streamlit for seamless interaction.

## 🛠️ Tech Stack
* **Programming Language:** Python 3
* **Data Manipulation & Analysis:** Pandas, NumPy
* **Natural Language Processing (NLP):** NLTK (PorterStemmer)
* **Machine Learning:** Scikit-Learn (CountVectorizer, Cosine Similarity)
* **Web Framework:** Streamlit
* **Environment:** Jupyter Notebook / VS Code

## 📊 Dataset
This project uses the famous **TMDB 5000 Movies Dataset** from Kaggle.
It involves merging two datasets based on the movie title:
* `tmdb_5000_movies.csv`
* `tmdb_5000_credits.csv`

## 🧠 How It Works (The Machine Learning Pipeline)
1. **Data Preprocessing:** Missing values are handled, and useful columns (`genres`, `id`, `keywords`, `title`, `overview`, `cast`, `crew`) are extracted.
2. **Feature Extraction:** JSON-like string data is parsed using `ast.literal_eval()`. Top 3 cast members and the director are filtered out.
3. **Tag Creation:** Spaces between names/words are removed (e.g., "James Cameron" becomes "JamesCameron") to avoid confusing first/last names. All text is merged into a single `tags` column and converted to lowercase.
4. **Stemming:** Words are reduced to their root forms (e.g., "actions", "acting", "acted" all become "act") using NLTK's `PorterStemmer`.
5. **Text Vectorization:** The `tags` are converted into a matrix of token counts using `CountVectorizer` (Bag of Words technique) with a maximum of 5000 features.
6. **Cosine Similarity:** The distance/angle between movie vectors is calculated. A smaller angle means higher similarity!

## 🚀 How to Run the Project Locally

### Prerequisites
Make sure you have Python installed on your system. It is highly recommended to use a virtual environment (like Anaconda or `venv`).

### 1. Clone the Repository
```bash
git clone https://github.com/vinay-271/Movie-Recommendation-System.git
cd Movie-Recommendation-System
```

### 2. Install Dependencies
Create a `requirements.txt` file (if you haven't already) containing `pandas`, `numpy`, `scikit-learn`, `nltk`, and `streamlit`. Then run:
```bash
pip install -r requirements.txt
```

### 3. Generate the Model/Pickle Files
Before running the Streamlit app, you need to execute the Jupyter Notebook (`movie-recommender-system.ipynb`) to process the data and generate the `.pkl` files (usually `movies.pkl` and `similarity.pkl`).
* Open the notebook.
* Run all cells.
* *(Note: Make sure your notebook ends with code that exports the pandas dataframe and the similarity matrix using the `pickle` library so Streamlit can read them).*

### 4. Run the Streamlit Web App
Once the model is ready, run the Streamlit application from your terminal:
```bash
streamlit run app.py
```
*(Note: Replace `app.py` with the actual name of your Python script if it is different).*

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.
---
*Created by @vinay-271 - Feel free to connect!*
