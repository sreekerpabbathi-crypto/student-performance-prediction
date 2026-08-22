# Student Performance Prediction

Predicts whether a student will Pass or Fail using machine learning, based on factors 
like study hours, attendance, previous marks, and assignment scores.

## Dataset

Uses the real **UCI Student Performance dataset** (Paulo Cortez, secondary school students 
from Portugal — 395 students). Original source: 
https://archive.ics.uci.edu/dataset/320/student+performance

The original UCI columns were renamed/derived to match this project's structure:

| Column used here | Derived from UCI |
|---|---|
| Study_Hours | `studytime` |
| Attendance | inverted `absences` |
| Previous_Marks | `G1` (1st period grade) |
| Internal_Marks | `G2` (2nd period grade) |
| Assignments | approximated from avg(G1, G2) — UCI has no direct assignments column |
| Socio_Economic_Status | combined `Medu` + `Fedu` (parents' education) |
| Final_Result | Pass if `G3 >= 10` (out of 20), else Fail |

## What it does

- Cleans and explores the data (missing values, correlations, class balance)
- Trains and compares 5 classification models: Logistic Regression, Decision Tree, 
  Random Forest, Naive Bayes, SVM
- Evaluates using accuracy, precision, recall, F1-score, and a confusion matrix
- Shows which features matter most (feature importance)
- Identifies at-risk students using only the held-out test set, so results reflect 
  genuine unseen-data performance
- Saves the trained model for reuse

## Tech stack

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn

## How to run

1. Open `projectttt.ipynb` in Google Colab or Jupyter Notebook
2. Make sure `student_data_real.csv` is in the same folder
3. Run all cells top to bottom

## Results

Random Forest generally performs best on this dataset. Internal marks and assignment 
scores turned out to be stronger predictors than raw attendance.

## Limitations

- 395 students is a fairly small dataset
- "Assignments" is an approximation, not an original UCI feature 
- Predictions reflect these two Portuguese schools specifically, may not generalize elsewhere
