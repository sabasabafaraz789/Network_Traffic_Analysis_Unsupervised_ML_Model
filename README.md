# Network_Traffic_Analysis_Unsupervised_ML_Model
---

## 📌 Model Overview

This project implements an **unsupervised network traffic analysis model** for detecting and analyzing cyber-attack patterns using **DBSCAN clustering** combined with **feature engineering and robust preprocessing** techniques.

---

## 🧠 Methodology

### 1️⃣ Data Preprocessing

* Network Intrusion dataset  from  [[CIC-IDS- 2017](https://www.kaggle.com/datasets/mrwellsdavid/unsw-nb15](https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset)):

  * Removing infinite values (`±inf`)
  * Dropping missing values
  * Removing duplicate records (label-aware)
* To ensure fair evaluation, the dataset is **balanced** by sampling an equal number of instances per attack class.

---

### 2️⃣ Feature Engineering

Several domain-specific features are engineered to better capture **network flow behavior**:

* **Fwd_Bwd_Pkts_Ratio** – Ratio of forward to backward packets
* **Total_Bytes** – Total bytes exchanged in a flow
* **Header_to_Data_Ratio** – Protocol header overhead relative to payload
* **Bwd_to_Fwd_Bytes_Ratio** – Traffic asymmetry indicator
* **Flow_IAT_Range** – Variability in inter-arrival times
* **Avg_IAT** – Average packet inter-arrival time
* **Packet_Size_Spread** – Difference between max and min packet sizes

These features help distinguish normal traffic from different attack behaviors.

---

### 4️⃣ Feature Scaling & Transformation

To handle skewed distributions and outliers:

* **PowerTransformer (Yeo-Johnson)** is applied for normalization
* **Min-Max Scaling** maps features into a uniform range
---

### 5️⃣ DBSCAN Clustering

The **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** algorithm is used because:

* It does **not require pre-defining the number of clusters**
* It can naturally identify **outliers/anomalies**
* It handles irregular cluster shapes common in network traffic data

#### Parameter Optimization

* A **k-distance plot** is used to estimate optimal `eps`
* A **grid search** over `eps` and `min_samples` evaluates:

  * Silhouette Score
  * Calinski-Harabasz Index
  * Noise ratio

The best parameters are selected based on clustering quality.

---

### 6️⃣ Cluster Evaluation

Clustering results are evaluated using:

* **Cluster purity** (dominant attack type per cluster)
* **Noise ratio** (percentage of detected anomalies)
* Mapping discovered clusters to known attack labels (for analysis only)

---

### 7️⃣ Visualization

* DBSCAN clusters are visualized in reduced space
* Noise points are highlighted separately
* Results are saved as figures for reporting and analysis

---

## 🚀 Key Highlights

* Unsupervised attack pattern discovery
* Robust feature engineering for network traffic
* Automatic anomaly detection via DBSCAN
* Balanced evaluation for fair comparison
* Interpretable cluster purity analysis

---

## 🛠️ Technologies Used

* Python
* Pandas, NumPy
* Scikit-learn
* Matplotlib / Seaborn

---

## 👨‍💻 Author
Developed by **Saba Faraz**  
📧 Email: farazsaba96@gmail.com

---
