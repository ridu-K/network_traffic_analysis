# 🚨 Network Traffic Anomaly Detection Using Machine Learning & Deep Learning

This project focuses on **detecting anomalies in network traffic data** using multiple **unsupervised and hybrid machine learning techniques**, including **Autoencoders**, **Isolation Forest + Random Forest**, and **K-Means clustering**. The dataset consists of packet-level network traffic captured in CSV format.

---

## 📌 Project Overview

* 📂 **Input Data**: Network traffic logs (`late.csv`)
* 🔍 **Goal**: Identify anomalous network packets
* 🧠 **Models Used**:

  * Deep Learning Autoencoder
  * Isolation Forest + Random Forest (Hybrid)
  * K-Means Clustering
* 📊 **Approach**: Unsupervised & semi-supervised anomaly detection
* 🖥️ **Platform**: Python (Google Colab / Local)

---

## 📁 Dataset Description

The dataset contains **117,084 network packets** with the following attributes:

| Column      | Description                                  |
| ----------- | -------------------------------------------- |
| No.         | Packet number                                |
| Time        | Timestamp of packet                          |
| Source      | Source IP address                            |
| Destination | Destination IP address                       |
| Protocol    | Network protocol (UDP, TCP, HTTP, TLS, etc.) |
| Length      | Packet length                                |
| Info        | Packet metadata                              |

---

## 🛠️ Tech Stack

* **Python**
* **Pandas & NumPy**
* **Scikit-learn**
* **TensorFlow / Keras**
* **Matplotlib**

---

## 🔎 Exploratory Data Analysis (EDA)

* Packet count and structure analysis
* Source & destination IP frequency analysis
* Protocol-wise traffic distribution
* Visualization of:

  * Top source IPs
  * Top destination IPs
  * Protocol usage
  * Packet length distribution

---

## 🧠 Model 1: Autoencoder-Based Anomaly Detection

### 🔧 Feature Engineering

* Selected features:

  * `Protocol` (One-Hot Encoded)
  * `Length`
* Feature scaling using **MinMaxScaler**

### 🏗️ Autoencoder Architecture

* Dense layers with ReLU activation
* Bottleneck encoding dimension: **10**
* Dropout layers for regularization
* Reconstruction loss: **Mean Squared Error (MSE)**

### ⚙️ Training Details

* Optimizer: Adam
* Epochs: 20
* Batch Size: 32

### 🚨 Anomaly Detection

* Reconstruction error calculated per packet
* Threshold set at **99.9th percentile**
* **88 anomalies detected**

---

## 🌲 Model 2: Isolation Forest + Random Forest (Hybrid)

### 🔧 Preprocessing

* Protocol encoded using **LabelEncoder**
* Features used:

  * `Protocol`
  * `Length`

### 🧠 Workflow

1. **Isolation Forest**

   * Identifies potential anomalies
   * Contamination rate: 0.45%
2. **Random Forest Classifier**

   * Learns anomaly patterns
   * Refines predictions

### 📌 Output

* **503 anomalies detected**
* Visualized using scatter plots (`Length vs Index`)

---

## 🔵 Model 3: K-Means Clustering for Anomaly Detection

### ⚙️ Steps

* Numeric feature selection
* Standardization using **StandardScaler**
* K-Means clustering (`k = 2`)
* Distance from cluster centroids used as anomaly score

### 🚨 Detection Strategy

* Top **0.1%** highest anomaly scores flagged
* **118 anomalies detected**

### 📊 Visualization

* Histogram of anomaly scores
* Clear separation between normal and anomalous packets

---

## 📈 Visualization Outputs

* Bar charts for protocol and IP frequencies
* Scatter plots highlighting anomalies
* Histogram of anomaly scores
* Comparative anomaly detection across models

---

## 📊 Results Summary

| Model                 | Anomalies Detected |
| --------------------- | ------------------ |
| Autoencoder           | 88                 |
| Isolation Forest + RF | 503                |
| K-Means               | 118                |

Each method captures **different anomaly characteristics**, improving overall reliability when combined.

---

## 🧪 Key Observations

* High packet lengths often correlate with anomalies
* TLS/SSL traffic frequently appears in anomalous clusters
* Autoencoders are effective for subtle deviations
* Tree-based models catch structural irregularities

---

## 🚀 How to Run

1. Install dependencies:

   ```bash
   pip install numpy pandas scikit-learn tensorflow matplotlib
   ```
2. Place `late.csv` in the project directory
3. Run the notebook / script sequentially
4. Visualize and inspect detected anomalies

---

## 📌 Applications

* Intrusion Detection Systems (IDS)
* Network traffic monitoring
* Cybersecurity threat analysis
* Abnormal traffic pattern detection
* Research in network anomaly detection

---

## 🔮 Future Enhancements

* Include time-based features
* Apply LSTM / Temporal Autoencoders
* Combine models using ensemble voting
* Real-time packet stream analysis
* Deploy using Flask / FastAPI
