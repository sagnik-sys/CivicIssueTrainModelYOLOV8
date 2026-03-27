<div align="center">

<!-- Banner -->
<img src="https://github.com/sagnik-sys/CivicIssueTrainModelYOLOV8/raw/main/Training%20Code%20and%20Outputs/runs/detect/train5/val_batch2_labels.jpg" alt="Detection Sample" width="100%" style="border-radius: 12px;" />

<br/><br/>

# 🚧 Civic Issue Detection System
### Real-Time Infrastructure Damage Detection via YOLOv8

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-FF4F00?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ultralytics/ultralytics)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

> **Automatically detect potholes, waterlogging, and damaged electric poles in real-time — enabling smarter, faster civic infrastructure maintenance.**

</div>

---

## 📖 Table of Contents

- [Project Overview](#-project-overview)
- [Demo](#-demo)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Model Architecture](#-model-architecture)
- [Performance](#-performance--evaluation)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Use Cases](#-use-cases)
- [Future Enhancements](#-future-enhancements)
- [License](#-license)

---

## 🌐 Project Overview

The **Civic Issue Detection System** is a computer vision solution built on **YOLOv8** that automatically identifies and classifies urban infrastructure damage from images and video streams.

Cities generate vast amounts of visual data every day — dashcam footage, surveillance feeds, citizen photos — yet much of it goes unanalyzed. This project bridges that gap by offering a **deployment-ready pipeline** that can:

- 🔍 Detect **potholes**, **waterlogged areas**, and **damaged electric poles**
- 🎥 Process both **static images** and **live video feeds**
- 📝 Produce **annotated outputs** with bounding boxes and confidence scores
- 🏗️ Scale to **smart city monitoring** systems with minimal integration effort

---

## 🎯 Demo

<div align="center">

| Input | Annotated Output |
|-------|-----------------|
| Raw road/infrastructure image | YOLOv8 detects and labels all damage with bounding boxes |

> *Annotated outputs are automatically saved to `Training Code and Outputs/runs/detect/`*

</div>

---

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| 🕒 **Real-Time Detection** | Processes images and video streams with fast inference |
| 🏷️ **Multi-Class Classification** | Simultaneously detects potholes, waterlogging, and damaged poles |
| 🖼️ **Annotated Output Generation** | Auto-saves labeled images and videos with bounding boxes |
| 🔄 **Data Augmentation** | Applies augmentation strategies to boost model robustness |
| 📦 **Pretrained Weights Included** | `best.pt` model checkpoint ready for immediate inference |
| 🔬 **Confidence Scoring** | Each detection includes a confidence score for filtering |
| 🧪 **End-to-End Notebook** | `Test.ipynb` covers the full inference workflow |

---

## 🛠️ Tech Stack

```
┌─────────────────────────────────────────────────────┐
│                 Civic Issue Detector                │
├─────────────────┬───────────────────────────────────┤
│  Core Model     │  YOLOv8 (Ultralytics)             │
│  Language       │  Python 3.8+                      │
│  Vision Library │  OpenCV                           │
│  Deep Learning  │  PyTorch (via Ultralytics)        │
│  Notebook       │  Jupyter Notebook                 │
│  Output Format  │  Annotated MP4 / JPG / PNG        │
└─────────────────┴───────────────────────────────────┘
```

---

## 🧠 Model Architecture

This system uses **YOLOv8** (You Only Look Once, Version 8) — a state-of-the-art single-stage object detector.

```
Input Image / Video Frame
         │
         ▼
  ┌─────────────┐
  │  YOLOv8     │  ← Backbone + Neck (CSPDarknet + PANet)
  │  Detector   │
  └──────┬──────┘
         │
         ▼
  Bounding Box Predictions + Class Labels + Confidence Scores
         │
         ▼
  ┌─────────────────────┐
  │  Annotated Output   │  ← Image / Video with drawn detections
  └─────────────────────┘
```

**Training Techniques Applied:**
- Custom dataset labeling with class-specific annotations
- Image normalization and preprocessing
- Data augmentation (flips, brightness shifts, mosaic)
- Confidence threshold tuning for optimal precision-recall trade-off

---

## 📊 Performance & Evaluation

| Metric | Value |
|--------|-------|
| 🎯 Detection Accuracy | ~75% on real-world test data |
| 🏷️ Classes Detected | Pothole, Waterlogging, Damaged Electric Pole |
| 📦 Model Format | `.pt` (PyTorch checkpoint) |
| 🔍 Evaluation Method | Visual validation + confidence score analysis |

> Training results and metric plots are available in `Training Code and Outputs/runs/detect/train5/`.

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- pip
- (Recommended) CUDA-enabled GPU for faster inference

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/sagnik-sys/CivicIssueTrainModelYOLOV8.git
cd CivicIssueTrainModelYOLOV8

# 2. Install dependencies
pip install ultralytics opencv-python

# 3. (Optional) Install Jupyter if not already installed
pip install notebook
```

### Running Inference

```bash
# Launch the test notebook
jupyter notebook Test.ipynb
```

Or run inference directly via Python:

```python
from ultralytics import YOLO

# Load the pretrained model
model = YOLO("best.pt")

# Run on an image
results = model("your_image.jpg")
results[0].show()  # Display annotated output

# Run on a video
results = model("your_video.mp4", save=True)
```

Annotated outputs will be saved automatically to the `runs/detect/` directory.

---

## 📁 Project Structure

```
CivicIssueTrainModelYOLOV8/
│
├── 📓 Test.ipynb                        # Inference notebook (run this!)
├── 🤖 best.pt                           # Trained YOLOv8 model weights
├── 📄 README.md
│
└── 📂 Training Code and Outputs/
    └── runs/
        └── detect/
            └── train5/
                ├── val_batch2_labels.jpg    # Validation batch with labels
                ├── results.png              # Training metrics plot
                └── ...                      # Other training artifacts
```

---

## 🏙️ Use Cases

- **Smart City Monitoring** — Integrate with city CCTV networks for automated damage reporting
- **Road Safety & Maintenance** — Flag critical potholes and waterlogged roads for priority repair
- **Utility Infrastructure Inspection** — Identify and log damaged electric poles at scale
- **Citizen Complaint Automation** — Build apps where user-submitted photos are auto-classified
- **Municipal Resource Planning** — Data-driven allocation of repair crews and budgets
- **Computer Vision Research** — A working baseline for domain-specific object detection projects

---

## 🔮 Future Enhancements

- [ ] 🗺️ **GPS-tagged detection reports** — Geo-locate detected issues on a city map
- [ ] 📊 **Damage severity estimation** — Classify severity (minor / moderate / critical)
- [ ] 🌐 **Web API / REST endpoint** — Deploy as a service for mobile/web app integration
- [ ] 📱 **Mobile-friendly inference** — Quantize model for on-device detection
- [ ] 🗃️ **Expanded dataset** — Add more civic issue classes (broken guardrails, garbage overflow, etc.)
- [ ] 🔔 **Alert system integration** — Auto-notify municipal authorities on detection

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve the model, extend the dataset, or add new features:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ for smarter, safer cities.

⭐ If you find this project useful, please consider giving it a star!

</div>
