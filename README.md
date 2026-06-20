# 🌳 WANARA Forest Fire Monitoring System

## Simulasi IoT Monitoring Kebakaran Hutan Berbasis AI

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![MQTT](https://img.shields.io/badge/MQTT-Public%20Broker-green.svg)
![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 📋 Tentang Proyek

Sistem simulasi monitoring kebakaran hutan dengan **25 node sensor** yang tersebar di berbagai taman nasional di Indonesia. Dilengkapi dengan **AI anomaly detection** dan **real-time MQTT publishing**.

---

## ✨ Fitur Utama

- ✅ **25 Node Sensor** di 25 Taman Nasional Indonesia
- 📡 **Real-time Data Streaming** via MQTT (broker.emqx.io)
- 🤖 **AI Anomaly Detection** untuk deteksi dini kebakaran
- 🌡️ **Simulasi Kondisi Realistis** (Suhu, Kelembaban, Asap)
- 📊 **Status:** NORMAL, WARNING, FIRE_ALERT
- 📶 **Kualitas Jaringan:** GOOD / POOR
- 🔄 **Automatic Reconnection** jika MQTT terputus
- 💤 **Node Offline Simulation** (1% chance per siklus)

---

## 🗺️ Daftar 25 Taman Nasional

| Node | Taman Nasional | Kecamatan | Provinsi |
|------|----------------|-----------|----------|
| node_1 | Gunung Leuser | Ketambe | Aceh |
| node_2 | Kerinci Seblat | Gunung Tujuh | Jambi |
| node_3 | Bukit Barisan Selatan | Bengkunat | Lampung |
| node_4 | Tanjung Puting | Kumai | Kalimantan Tengah |
| node_5 | Kayan Mentarang | Mentarang | Kalimantan Utara |
| node_6 | Lore Lindu | Sigi Biromaru | Sulawesi Tengah |
| node_7 | Aketajawe Lolobata | Wasile | Maluku Utara |
| node_8 | Wasur | Merauke | Papua Selatan |
| node_9 | Ujung Kulon | Sumur | Banten |
| node_10 | Baluran | Banyuputih | Jawa Timur |
| node_11 | Meru Betiri | Tempurejo | Jawa Timur |
| node_12 | Alas Purwo | Tegaldlimo | Jawa Timur |
| node_13 | Bromo Tengger Semeru | Sukapura | Jawa Timur |
| node_14 | Sebangau | Sebangau Kuala | Kalimantan Tengah |
| node_15 | Danau Sentarum | Batang Lupar | Kalimantan Barat |
| node_16 | Kutai | Teluk Pandan | Kalimantan Timur |
| node_17 | Betung Kerihun | Putussibau Utara | Kalimantan Barat |
| node_18 | Bukit Baka Bukit Raya | Serawai | Kalimantan Barat |
| node_19 | Bogani Nani Wartabone | Suwawa | Gorontalo |
| node_20 | Rawa Aopa Watumohai | Aopa | Sulawesi Tenggara |
| node_21 | Bantimurung Bulusaraung | Bantimurung | Sulawesi Selatan |
| node_22 | Manusela | Tehoru | Maluku |
| node_23 | Lorentz | Kwamki Narama | Papua Tengah |
| node_24 | Teluk Cenderawasih | Rumberpon | Papua Barat |
| node_25 | Cycloop | Sentani Timur | Papua |

---

## 🚀 Cara Menjalankan

### 1. Clone Repository
```bash
git clone https://github.com/riskydavid25/dummy-wanara-web-monitoring.git
cd dummy-wanara-web-monitoring
```

### 2. Install Dependencies
```bash
pip install paho-mqtt
```

### 3. Jalankan Simulator
```bash
python Dummy_Node_Wanara.ipynb
```

Atau buka langsung di **Google Colab** / **Jupyter Notebook**.

---

## 📊 Format Data MQTT

**Topic:** `wanara/{node_id}`

**Payload (JSON):**
```json
{
  "node_id": "node_1",
  "node_name": "Node 1",
  "forest_name": "Hutan Taman Nasional Gunung Leuser",
  "latitude": 3.758,
  "longitude": 97.13,
  "district": "Ketambe",
  "city": "Aceh Tenggara",
  "province": "Aceh",
  "temperature": 34.5,
  "humidity": 65.2,
  "fire_detected": false,
  "smoke_level": 21,
  "status": "NORMAL",
  "qos": {
    "network_status": "GOOD",
    "signal_strength_dbm": -72,
    "latency_ms": 45,
    "packet_loss_percent": 0.5
  },
  "timestamp": "2026-06-20 14:30:15"
}
```

### Status Conditions

| Status | Temperature | Humidity | Smoke Level | Keterangan |
|--------|-------------|----------|-------------|------------|
| NORMAL | 24-42°C | 45-90% | 10-250 ppm | Kondisi aman |
| WARNING | Variatif | Variatif | Variatif | Potensi bahaya |
| FIRE_ALERT | 45-65°C | 15-40% | 300-800 ppm | 🔥 KEBAKARAN! |

---

## ⚙️ Parameter Simulasi

| Parameter | Nilai |
|-----------|-------|
| Total Node | 25 |
| Delay Antar Node | 0.4 detik |
| Siklus Penuh | ~20 detik |
| MQTT Broker | broker.emqx.io |
| Port | 1883 |
| QoS | 1 |
| Keepalive | 60 detik |
| Chance FIRE_ALERT | 8% per node per siklus |
| Chance Node Offline | 1% per node per siklus |

---

## 🛠️ Teknologi yang Digunakan

- Python 3.x
- paho-mqtt - MQTT Client Library
- JSON - Data Serialization
- Random - Data Generation
- Datetime - Timestamp Management

---

## 📈 Contoh Output

```
============================================================
WANARA FOREST FIRE MONITORING SIMULATOR RUNNING (AI MODE)
============================================================
TOTAL NODE : 25
DELAY      : 0.4 detik antar node (cegah drop MQTT)
INTERVAL   : ~20 detik per siklus penuh
============================================================
✅ Connected to MQTT Broker!
[OK]   node_1 | NORMAL     | 34.5°C | 21 ppm
[OK]   node_2 | FIRE_ALERT | 61.8°C | 711 ppm
[OK]   node_3 | WARNING    | 39.2°C | 241 ppm
💤 node_19 simulasi offline 54s

📊 Siklus selesai — Terkirim: 24 | Dilewati: 1
⏳ Jeda 10 detik sebelum siklus berikutnya...
```

---

## 🔧 Konfigurasi

### Mengubah Broker MQTT
```python
BROKER = "broker.emqx.io"  # Ganti dengan broker Anda
PORT   = 1883
```

### Mengubah Jumlah Node
Edit array `nodes` untuk menambah/mengurangi node sensor.

### Mengubah Probabilitas Kejadian
```python
fire_detected = random.random() < 0.08  # 8% chance kebakaran
if random.random() < 0.01:              # 1% chance offline
```

---

## 🐛 Troubleshooting

| Masalah | Solusi |
|---------|--------|
| MQTT Connection Failed | Pastikan internet terhubung, coba ganti broker: broker.hivemq.com atau test.mosquitto.org |
| Data Tidak Masuk Dashboard | Periksa subscription topic: wanara/#, pastikan QoS 1 |
| Deprecation Warning | Abaikan, masih compatible dengan versi terbaru |

---

## 🤝 Kontribusi

Silakan fork repository ini dan buat pull request untuk perbaikan atau penambahan fitur.

### Ide Pengembangan:
- [ ] Tambahan node di seluruh Indonesia
- [ ] Integrasi dengan dashboard real-time (Grafana)
- [ ] Simulasi cuaca (angin, curah hujan)
- [ ] Database storage (InfluxDB/TimescaleDB)
- [ ] Notifikasi (Telegram/Email) untuk FIRE_ALERT

---

## 📄 Lisensi

MIT License - Silakan gunakan dan modifikasi untuk keperluan pembelajaran dan penelitian.

---

## 📞 Kontak

- **Email:** riskydavidkasyanto25@gmail.com
- **GitHub:** [riskydavid25](https://github.com/riskydavid25)

---

**🌿 Jaga Hutan Kita, Cegah Kebakaran!**
