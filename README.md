# Laptop Price Prediction — Machine Learning Web Application

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python) ![Flask](https://img.shields.io/badge/Flask-Web_App-black?logo=flask) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Machine_Learning-orange?logo=scikitlearn) ![Vercel](https://img.shields.io/badge/Vercel-Deployment-black?logo=vercel)

**An interactive machine learning prediction dashboard built with Python, Flask, and Chart.js.**

**[Live Demo](https://laptop-price-prediction-aws.vercel.app/)** · **[GitHub Repository](https://github.com/yashchaudhari372-lab/Laptop_Price_Prediction_Aws)**

## Overview

This project demonstrates how to serve a pre-trained, serialized machine learning model through a Flask web application. Users enter five attributes, submit a prediction request, and see the model's output in a responsive analytics interface.

> **Important implementation note:** Although the repository is named *Laptop Price Prediction*, the current `app.py` passes **Age, Gender, Region, Occupation, and Income** to the model. These are demographic/economic inputs, not laptop specifications such as RAM, CPU, storage, or GPU. The repository does not currently provide the training dataset or a verified explanation of the target variable. Verify the model's actual prediction target before presenting the output as a laptop price estimate.

## Key Features

- **Model-powered predictions:** Loads the saved `_model.pkl` file and calls its `predict()` method.
- **Interactive form:** Accepts five numerical or encoded input fields.
- **Visual analytics:** Uses Chart.js to display input-related information.
- **Responsive interface:** HTML and CSS are embedded directly in the Flask application.
- **Theme switcher:** Supports dark and light appearance modes.
- **Error handling:** Displays an error if the model cannot load or a prediction fails.
- **Online demonstration:** Live app linked through Vercel.

## Technology Stack

| Layer | Technologies |
| --- | --- |
| Programming language | Python |
| Web framework | Flask |
| ML inference | Scikit-learn-compatible serialized model, Pickle |
| Data processing | Pandas, NumPy |
| Frontend | HTML, CSS, JavaScript |
| Charts | Chart.js |
| Hosting | Vercel (live application link) |

## Current Model Inputs

| Feature | Description |
| --- | --- |
| `Age` | User-provided age |
| `Gender` | Numerically encoded gender |
| `Region` | Numerically encoded region |
| `Occupation` | Numerically encoded occupation |
| `Income` | User-provided income |

**Note:** The exact encoding mappings, training transformations, target definition, and valid feature ranges should be confirmed from the original training notebook or dataset. The application currently converts these five inputs to floating-point values before prediction.

## Prediction Workflow

```text
User opens the dashboard
          |
          v
Enters Age, Gender, Region, Occupation, Income
          |
          v
Flask receives POST /predict
          |
          v
Pandas DataFrame with five named features
          |
          v
Saved model (_model.pkl) runs predict()
          |
          v
Prediction result shown in dashboard
```

## Repository Structure

```text
Laptop_Price_Prediction_Aws/
├── app.py             # Flask application, HTML/CSS/JS and inference logic
├── _model.pkl         # Serialized trained model
├── requirements.txt   # Python dependencies
└── README.md          # Project documentation
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/yashchaudhari372-lab/Laptop_Price_Prediction_Aws.git
cd Laptop_Price_Prediction_Aws
```

### 2. Create and activate a virtual environment

**Windows:**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

The repository's `requirements.txt` lists Flask, scikit-learn, NumPy, and Pandas. A compatible scikit-learn version may be necessary to deserialize the original model.

### 4. Start the application

```bash
python app.py
```

Open **http://127.0.0.1:5000/** in your browser.

> Only load `.pkl` model files from sources you trust: unpickling can execute arbitrary code.

## Routes

| Method | Route | Purpose |
| --- | --- | --- |
| GET | `/` | Displays the prediction dashboard |
| POST | `/predict` | Accepts HTML form fields, runs the model, and returns the rendered result page |

### Example form submission

```bash
curl -X POST http://127.0.0.1:5000/predict \
  -d "Age=30" \
  -d "Gender=1" \
  -d "Region=1" \
  -d "Occupation=2" \
  -d "Income=50000"
```

The response is **HTML**, not a JSON API. The example values are illustrative and are not verified training-domain encodings.

## Model Evaluation

The public repository includes the serialized model but does not establish independently verified performance results or a reproducible test split.

| Metric | Status |
| --- | --- |
| Model type | Described as Decision Tree in `app.py`; verify from saved estimator |
| R² | 75.0% |
| Mean Absolute Error (MAE) | 67.0% |
| Root Mean Squared Error (RMSE) | 75.0% |

If the underlying task is regression, evaluate predictions on a held-out test dataset and report R², MAE, and RMSE. Do not use classification accuracy as a regression metric.

## Screenshots

Add screenshots of the application to an `assets/` folder, then uncomment these lines:

```markdown
<!-- ![Dashboard](assets/dashboard.png) -->
<!-- ![Prediction result](assets/prediction-result.png) -->
```

## Future Improvements

- Confirm and document the trained model's target variable and input encodings.
- If the intended task is laptop price estimation, train or retrain using laptop hardware features (brand, processor, RAM, storage, GPU, display, etc.).
- Add a reproducible training notebook, dataset provenance, and evaluation metrics.
- Save preprocessing and model inference together in a versioned pipeline.
- Improve input validation and show human-readable feature labels.
- Add automated tests and pinned dependency versions.
- Rename the repository or interface if the model predicts a different outcome.

## Developer

**Yash Chaudhari** — Aspiring Data Scientist & Data Analyst

- [GitHub](https://github.com/yashchaudhari372-lab)
- [LinkedIn](https://www.linkedin.com/in/yashchaudhari08/)

## Disclaimer

This project is a machine learning demonstration. Predictions depend on the original training data, encoding scheme, and model quality; do not treat outputs as independently validated market prices.
