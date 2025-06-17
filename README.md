![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)

# Deployment of a Cloud-Integrated Building Management System for Environmental Monitoring in Medical Laboratories Using Node-RED

## Project Overview

This project demonstrates the simulation, monitoring, alerting, and cloud-based storage of environmental sensor data in a medical laboratory setting using Node-RED. The system emulates key environmental parameters such as temperature, humidity, and air quality—critical for ensuring safe and compliant lab conditions. It features a real-time dashboard for visualising sensor data, stores readings in Google Sheets and Google Firestore for traceability and auditing, and sends automated email alerts when predefined safety thresholds are exceeded, supporting timely interventions and regulatory compliance.

---

## Project Components

### 1. Sensor Data Simulation
- Randomly generated values for:
  - **Temperature**: between 20°C and 35°C
  - **Humidity**: between 30% and 70%
  - **Air Quality Index (AQI)**: between 0 and 150

### 2. Data Validation and Classification
- **Validation Node**: Checks if temperature exceeds 50°C or humidity exceeds 90%, triggering internal alerts.
- **Air Quality Classification Node**:
  - `Good` if AQI ≤ 50
  - `Moderate` if AQI between 51 and 100
  - `Bad` if AQI > 100

### 3. Alert System
- Checks for:
  - High temperature (>30°C)
  - Low humidity (<35%)
  - High humidity (>65%)
  - Poor air quality (>100 AQI)
- Generates human-readable alert messages.

### 4. Data Storage
- **Google Sheets**: Appends each new sensor reading to a sheet named "SensorData" with fields for temperature, humidity, air quality, air quality level, and any triggered alerts.
- **Google Firestore**: Saves each reading in a Firestore collection named `sensor_readings`, storing structured sensor data.

### 5. Live Dashboard Visualisation
- Built with Node-RED Dashboard components:
  - **Radar Chart** visualises all three parameters (temperature, humidity, air quality) in real-time.
- The dashboard automatically updates with each new injected sensor reading.

### 6. Email Notifications
- **Automatic Email Alerts**:
  - If any alert conditions are met, an email is sent automatically.
  - Configured using Gmail SMTP and an App Password for secure sending.
  - Email subject: 🚨 Sensor Alert Notification!

---

## Project Flow Summary

1. **Inject Node** generates or triggers sensor data simulation.
2. **Generate Random Sensor Data Node** creates random values.
3. **Validate Data Node** checks for extreme values.
4. **Classify Air Quality Node** assigns air quality level.
5. **Temperature and Other Alerts Node** checks thresholds and prepares alert messages.
6. **Parallel Paths**:
   - **Google Sheets Upload**: Sends flattened data to a Google Sheets document.
   - **Firestore Upload**: Sends structured data to Firestore.
   - **Chart Visualisation**: Prepares and sends data to the radar chart.
   - **Email Alerts**: Sends email if alerts exist.

---

## Technologies Used

- **Node-RED** (Local deployment)
- **Node-RED Dashboard**
- **Google Cloud Firestore**
- **Google Sheets (via API)**
- **SMTP Email (Gmail App Password)**
- **JavaScript for Function Nodes**

---

## How to Run

1. Install Node-RED and required nodes:
   - node-red-dashboard
   - node-red-node-email
   - node-red-contrib-google-cloud
   - node-red-contrib-google-sheets-advance

2. Configure your credentials:
   - Google Service Account JSON file for Firestore.
   - OAuth2 credentials for Google Sheets.
   - App Password for Gmail SMTP.

3. Deploy the Node-RED flow.

4. Open the Dashboard at:
   ```http://(local_server)/ui```

5. Click Inject to simulate new data and observe live updates, cloud storage, and email alerts.

---

## Example Visuals

- **Live Dashboard Radar Chart**: Displays live sensor readings.
- **Google Sheets Table**: Stores historical sensor readings.
- **Firestore Collection**: Structured JSON documents.
- **Email Alerts**: Notification when thresholds are crossed.

---

## Future Improvements

- Automatically schedule data injection (e.g., every 5 minutes).
- Add authentication for Node-RED dashboard users.
- Implement predictive analytics or ML anomaly detection.
- Extend dashboard with historical trend charts.

---

## Author

- **Built as part of a Cloud and Distributed Computing coursework project at Flinders University.**
- **Node-RED version:** 4.0.9
- **Environment:** Windows 10, local Node-RED deployment.

---

Thank you for checking out this project!

## License

This project is licensed under the [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](https://creativecommons.org/licenses/by-nc-nd/4.0/).

© 2025 Selin Cildir. All rights reserved.

You may:
- View and share this project for personal learning or reference.

You may **not**:
- Use this project or its code for academic, research, commercial, or professional purposes.
- Modify, remix, or redistribute any part of the codebase without explicit written permission.

Full attribution is required in any reference to this work.




