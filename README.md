# ECG-Based Multiple Disease Prediction

Predicting Heart Disease, Diabetes, and Parkinson's Disease using trained ML models, with a real ECG sensor that measures heart parameters automatically instead of entering them manually.


---

## Diseases & Models

### ❤️ Heart Disease
- **Model:** Logistic Regression
- **Dataset:** [Cleveland Heart Disease Dataset](https://github.com/siddhardhan23/multiple-disease-prediction-streamlit-app/tree/main/dataset)
- **Features:** Age, sex, chest pain type, resting BP, cholesterol, fasting blood sugar, max heart rate, ST depression, resting ECG result, exercise-induced angina, major vessels, thal
- **ECG sensor measures:** Max Heart Rate · ST Depression · Resting ECG Result
- **Entered manually:** Everything else

### 🩸 Diabetes
- **Model:** Logistic Regression
- **Dataset:** [Pima Indians Diabetes Dataset](https://github.com/siddhardhan23/multiple-disease-prediction-streamlit-app/tree/main/dataset)
- **Features:** Pregnancies, glucose, blood pressure, skin thickness, insulin, BMI, diabetes pedigree function, age
- **All fields entered manually**

### 🧠 Parkinson's Disease
- **Model:** SVM (linear kernel)
- **Dataset:** [UCI Parkinson's Dataset](https://github.com/siddhardhan23/multiple-disease-prediction-streamlit-app/tree/main/dataset)
- **Features:** MDVP:Fo, MDVP:Fhi, MDVP:Flo, Jitter, Shimmer, NHR, HNR, RPDE, DFA, spread1, spread2, D2, PPE
- **All fields entered manually**

---

## How the ECG Integration Works

Patient wears ECG electrodes
│
▼
AD8232 sensor captures heart electrical activity
│
▼
ESP32 streams raw signal over WiFi
│
▼
Python extracts clinical features:
→ Heart Rate (BPM)
→ ST Depression
→ Resting ECG Result
│
▼
Model predicts heart disease risk

---

## Hardware

<img width="327" height="581" alt="image" src="https://github.com/user-attachments/assets/e2b2dad6-3a02-41bf-bd4d-5981febe1283" />


| Component | Role |
|---|---|
| AD8232 | Captures raw ECG signal |
| ESP32 | Reads & streams signal over WiFi |
| 3-lead electrodes | RA, LA, RL chest placement |

**Wiring:**

| AD8232 | ESP32 |
|---|---|
| 3.3V | 3.3V |
| GND | GND |
| OUTPUT | GPIO34 |
| LO- | GPIO32 |
| LO+ | GPIO33 |

---

## Demo Interface (Streamlit)

<img width="1009" height="478" alt="image" src="https://github.com/user-attachments/assets/447a9282-feba-4ee6-92ae-082e0228588e" />

The app brings all three modules together. For heart disease, clicking **"Measure with ECG Sensor"** triggers a 10-second reading and auto-fills the sensor-derived fields. Diabetes and Parkinson's use manual input.

---

## Run It

```bash
pip install streamlit scikit-learn numpy pandas scipy websockets
streamlit run app/app.py
```

---

## Limitations

- Single-lead ECG is an approximation — not a substitute for clinical 12-lead measurement
- Models trained on small datasets — not validated for clinical use
- For research and learning purposes only

---

## Stack

`Python` · `scikit-learn` · `ESP32` · `AD8232` · `Streamlit` · `WebSocket`
