🧠 Sentiment Analysis with OCR, Machine Learning & Gradio UI

This project is an end-to-end sentiment-analysis system capable of classifying text from Twitter, Reddit, and images via OCR. It includes a full preprocessing pipeline, multiple ML classifiers, confusion-matrix visualizations, and an interactive Gradio web interface supporting both text input and image uploads.

📌 Features ✅ Text Sentiment Analysis ✅ Image → OCR → Sentiment Classification ✅ Multiple ML Models Trained & Benchmarked ✅ Confusion Matrices for Every Model ✅ Gradio UI for Real-Time Predictions ✅ Saved Models for Reuse (joblib) 📁 Project Workflow

Data Preprocessing
The pipeline performs:

URL, punctuation, emoji removal

Lowercasing & whitespace normalization

Stop-word removal

Word tokenization

Lemmatization

Dataset-specific cleaning rules

TF-IDF feature extraction

Processed features are saved automatically.

📊 Model Training & Evaluation

Two datasets were trained separately:

Twitter_Data.csv (sentiment labels: -1, 0, 1)

Reddit_Depression Dataset (binary sentiment classification)

For each dataset, the following models were trained:

Linear SVM (LinearSVC)

Logistic Regression

Random Forest

Multinomial Naive Bayes

📈 Twitter Dataset Results (162,980 rows) Performance Summary Model Accuracy Precision Recall F1 Score ROC-AUC LinearSVC 0.8939 0.8941 0.8939 0.8931 — LogisticRegression 0.8788 0.8800 0.8788 0.8773 0.9599 RandomForest 0.8497 0.8510 0.8497 0.8459 0.9515 MultinomialNB 0.7266 0.7449 0.7266 0.7180 0.8994 Classification Report Accuracy: 0.89
Macro F1: 0.88
Weighted F1: 0.89

Class Performance

Negative (-1) → Precision 0.87 | Recall 0.80

Neutral (0) → Precision 0.88 | Recall 0.95

Positive (1) → Precision 0.92 | Recall 0.90

Confusion Matrix Overview

Each model’s confusion matrix shows:

LinearSVC had the best separation, especially between Neutral vs Positive.

Most misclassifications occurred between Neutral ↔️ Negative due to similar wording.

Naive Bayes confused Positive/Negative heavily due to TF-IDF sensitivity.

📈 Reddit Dataset Results (depression_dataset_reddit_cleaned.csv) Performance Summary Model Accuracy Precision Recall F1 Score ROC-AUC LinearSVC 0.9638 0.9639 0.9638 0.9637 — LogisticRegression 0.9599 0.9604 0.9599 0.9599 — RandomForest 0.9579 0.9604 0.9579 0.9579 — MultinomialNB 0.8862 0.9036 0.8862 0.8851 — Classification Report Accuracy: 0.96
Macro F1: 0.96
Weighted F1: 0.96

Class Performance

Class 0 → F1: 0.96

Class 1 → F1: 0.96

Confusion Matrix Overview

LinearSVC had nearly perfect separation.

Very balanced dataset → high precision & recall for both classes.

NB underperformed due to TF-IDF sparsity.

🖼 OCR + Image Sentiment Analysis

The project integrates Tesseract OCR:

✔ Upload any image

(Screenshot, meme, photo, scanned document)

✔ OCR extracts visible text

Converts to grayscale

Applies preprocessing

Extracts text

Cleans the text using the same NLP logic

✔ Cleaned text is passed to the ML model

Sentiment predicted

Debug mode shows extracted text

OCR is especially useful for:

Social-media screenshots

Quotes

Posters

Memes

Mobile photos

🖥 Gradio User Interface (UI)

A unified Gradio UI provides two modes:

1️⃣ Text Input Mode

Type any sentence

Choose dataset (Twitter or Reddit)

Choose model (Best, SVM, LR, etc.)

Instant prediction provided in JSON format

2️⃣ Image Upload Mode

Upload PNG/JPG images

OCR extracts text automatically

Text is classified using the selected model

Helpful for screenshots & meme analysis

UI Features

Clean layout

Supports both inputs simultaneously

Displays OCR text for validation

Mobile-friendly

"Share=True" allows public hosting

🚀 Running the Project

Install dependencies pip install -r requirements.txt

Launch Notebook

Run all cells inside Google Colab / Jupyter.

Start Gradio App
