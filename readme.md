# 🌱 Soil Classification Challenge — Annam.AI x IIT Ropar

This repository contains my solutions for the **Soil Image Classification Challenge**, a two-part Kaggle competition hosted by **Annam.AI (IIT Ropar)** as an initial task for shortlisted hackathon participants.

| | |
|---|---|
| **Host** | Annam.AI, IIT Ropar |
| **Platform** | Kaggle (Community Prediction Competition — Private) |
| **Prize** | Kudos (does not award Points or Medals) |
| **Repo contents** | Challenge PDF, Part 1 solution notebook/script, Part 2 solution notebook/script |

---

## 📑 Table of Contents

- [Overview](#overview)
- [Part 1: Soil Classification (4-class)](#part-1-soil-classification-4-class)
- [Part 2: Soil Classification (Binary)](#part-2-soil-classification-binary)
- [Evaluation Metric](#evaluation-metric)
- [Dataset Structure](#dataset-structure)
- [Results](#results)
- [Repository Structure](#repository-structure)
- [Approach](#approach)
- [Part 1 — Code Details (`Part-1.ipynb`)](#part-1--code-details-part-1ipynb)
- [Part 2 — Code Details (`Part-2.ipynb`)](#part-2--code-details-part-2ipynb)


---

## Overview

Soil plays a foundational role in agriculture and the environment. Healthy soils support plant growth and food production, so being able to quickly and accurately identify soil type is valuable for crop management, land use planning, and environmental assessment. Soil classification is considered a "burgeoning field" with importance across farming, geology, and engineering.

Participants apply computer vision and machine learning techniques (typically a CNN) on labeled soil images to predict soil type from a photograph, using features like color, texture, and patterns.

**Common preprocessing guidance across both parts:**
- Split data into training/validation sets and tune the model accordingly.
- Standardize image dimensions (e.g., resize/crop to 224×224 pixels) for compatibility with common neural network architectures.
- Normalize pixel values and apply augmentation as needed.
- Ensure consistent formatting and sufficient data cleaning (e.g., handling brightness or background variations).
- Submit clean, well-documented, reproducible code — code quality, organization, and documentation are part of the judging criteria, in addition to the numeric score.

---

## Part 1: Soil Classification (4-class)

**Competition:** *Soil Classification*
**Task:** Classify each provided soil image into one of **four soil types**: Alluvial soil, Black soil, Clay soil, or Red soil.

| Detail | Value |
|---|---|
| Start | May 19, 2025 |
| Deadline / Close | May 25, 2025, 11:59 PM IST |
| Entrants | 502 |
| Participants | 389 |
| Teams | 169 |
| Submissions | 514 |
| Tag | Custom Metric |

**Dataset**

| Detail | Value |
|---|---|
| Files | 1,566 |
| Size | 153.18 MB |
| Type | jpg, jpeg, png, + 3 others |
| License | MIT |

- **Training set:** images + a CSV with columns `image_id` (unique identifier) and `soil_type` (ground-truth label).
- **Test set:** images with a CSV listing `image_id` for each test image (no labels provided); predictions must be submitted in the required format.
- Images are organized into separate `train/` and `test/` directories; sizes vary from small to large resolutions.

**Folder layout (`soil_classification-2025/`):**
```
soil_classification-2025/
├── train/                  # 1,222 files
├── test/                   # 341 files
├── sample_submission.csv   # 185 B
├── test_ids.csv             # 5.84 kB
└── train_labels.csv         # 35.19 kB
```

**Classes:** Alluvial soil · Black soil · Clay soil · Red soil

**Notes from the organizers:**
- Ensure the model handles all classes well — the evaluation metric focuses on balanced performance across classes.
- Preprocess images to account for varying sizes and ensure compatibility with the model.
- Use only the training set for model training; the test set is for evaluation purposes only (using test images for training violates competition rules).

---

## Part 2: Soil Classification (Binary)

**Competition:** *Soil Classification — Part 2*
**Task:** Classify each image as **soil image or not** (binary classification). This is "assignment number 2" for the soil classification challenge.

| Detail | Value |
|---|---|
| Start | May 21, 2025 |
| Deadline / Close | May 25, 2025, 11:59 PM IST |
| Entrants | 378 |
| Participants | 319 |
| Teams | 140 |
| Submissions | 402 |
| Tag | F1 Score |

**Dataset**

| Detail | Value |
|---|---|
| Files | 2,192 |
| Size | 145.86 MB |
| Type | jpg, jpeg, png, + 3 others |
| License | Unset |

- **Training set:** images + a CSV with columns `image_id` and `soil_type`.
- **Test set:** images are **not public**; a CSV lists `image_id` for each test image; predictions submitted in the required format.
- Images organized into a `train/` directory; participants preprocess as needed.

**Folder layout (`soil_competition-2025/`):**
```
soil_competition-2025/
├── train/                  # 1,222 files
├── test/                   # 967 files
├── sample_submission.csv   # 172 B
├── test_ids.csv             # 35.79 kB
└── train_labels.csv         # 23.33 kB
```

**Classes referenced in the source dataset:** Alluvial soil · Black soil · Clay soil · Red soil (the task itself is framed as binary — soil vs. not-soil — per the competition description).

**Notes from the organizers:**
- Preprocess images to account for varying sizes and ensure compatibility with the model.
- Use only the training set for model training; the test set is for evaluation purposes only.
- This dataset provides a foundational challenge for soil classification, with future training levels introducing additional complexities.

---

## Evaluation Metric

Both parts use **F1-score** as the base metric, with Part 1 extending it to a balanced multi-class form:

- **Part 1 — Minimum F1-score across all classes (maximize).** The model is scored by computing the F1-score for each of the four soil categories, then taking the **minimum** of those four F1-scores. This encourages models to perform well on every soil type, not just on average, and penalizes classifiers with an imbalance between precision and recall.
- **Part 2 — F1-score for binary classification (maximize).**

**Why F1:** The F1-score is the harmonic mean of precision and recall, ranging from 0 (worst) to 1 (best). An F1 of 1.0 for a class means perfect precision and recall on that class; an F1 of 0 indicates complete failure (either precision or recall is zero).

**Additional assessment (both parts):** Besides the numeric score, final evaluation includes a review of submitted notebooks — clear logic, thorough comments, code quality, organization, and documentation are part of the judging criteria.

**Submission requirements (both parts):** Submit predictions via the competition platform by the deadline, along with a well-documented code notebook/script that includes preprocessing, training, evaluation, and final-prediction generation, with clear comments and explanations.

---

## Dataset Structure

```
Part 1 — soil_classification-2025/     Part 2 — soil_competition-2025/
├── train/  (1,222 files)               ├── train/  (1,222 files)
├── test/   (341 files)                 ├── test/   (967 files)
├── sample_submission.csv               ├── sample_submission.csv
├── test_ids.csv                        ├── test_ids.csv
└── train_labels.csv                    └── train_labels.csv
```

Common columns:
- `image_id` — unique identifier for each image
- `soil_type` — ground-truth label (training data only)

---

## Results

Final standings on the **private leaderboard** (calculated on ~70% of the test data; competitions have completed):

| Challenge | Rank | Team | Score | Entries | Rank Δ |
|---|---|---|---|---|---|
| Part 1 (4-class) | 109 | Virendra Badgotya | **0.9610** | 4 | ▲57 |
| Part 2 (Binary) | 50 | Virendra Badgotya | **0.8666** | 4 | ▲12 |

---

## Repository Structure

```
.
├── README.md
├── Soil_Classification_challenge.pdf     # Original challenge brief (this doc's source)
├── Part-1_Code.ipynb                          # 4-class soil classification solution (ResNet18)
└── Part-2_Code.ipynb                          # Binary soil classification solution (ResNet18 features + One-Class SVM)
```

---

## Approach

At a high level:

- **Part 1** is a supervised 4-class problem, tackled with a **fine-tuned ResNet18 classifier** trained end-to-end on the labeled soil images.
- **Part 2** is framed as a **one-class / novelty-detection problem** — only "soil" images are available for training, so a pretrained **ResNet18 is used purely as a frozen feature extractor**, and a **One-Class SVM** learns the boundary of "soil-like" images to flag test images as soil (inlier) vs. not-soil (outlier).

---

## Part 1 — Code Details (`Part-1.ipynb`)

**Framework:** PyTorch / torchvision

**1. Imports & setup** — `pandas`, `numpy`, `scikit-learn` (`f1_score`, `classification_report`, `train_test_split`), `torch`, `torchvision.transforms/models`, `PIL.Image`, `tqdm`.

**2. Paths** — reads directly from the Kaggle input mount:
`/kaggle/input/soil-classification/soil_classification-2025/` (`train/`, `test/`, `train_labels.csv`, `test_ids.csv`).

**3. Label encoding & split**
- Builds a `label_mapping` dict (`soil_type` → integer index) and its inverse for decoding predictions.
- **Stratified train/validation split**: 85% train / 15% validation (`test_size=0.15`, `stratify=df['label']`, `random_state=42`).

**4. Image transforms** (via `torchvision.transforms`):
- Train: `Resize(224, 224)` → `RandomHorizontalFlip()` → `RandomRotation(15)` → `ToTensor()` → `Normalize(mean=[0.5]*3, std=[0.5]*3)`.
- Val/Test: `Resize(224, 224)` → `ToTensor()` → `Normalize(mean=[0.5]*3, std=[0.5]*3)` (no augmentation).

**5. Custom `SoilDataset`** — a `torch.utils.data.Dataset` that loads an image by `image_id`, converts to RGB, applies the transform, and returns `(image, label)` for train/val or `(image, image_id)` for test.

**6. Model**
- **ResNet18** pretrained on ImageNet (`models.resnet18(pretrained=True)`).
- Final fully-connected layer replaced with `nn.Linear(in_features, num_classes)` (4 soil classes).
- Loss: `CrossEntropyLoss`. Optimizer: `Adam`, learning rate `1e-4`.
- `DataLoader` batch size: 32 (train shuffled, val not shuffled).

**7. Training loop**
- **10 epochs**, standard forward/backward/optimizer-step loop with `tqdm` progress bars.
- After each epoch, runs validation and computes **per-class F1-score** for all 4 classes, then reports the **minimum F1 across classes** — matching the competition's official metric.

**8. Inference & submission**
- Loads `test_ids.csv`, runs the trained model over the test set (no augmentation), argmax's the logits to get predicted class indices, and maps them back to soil-type strings via the inverse label mapping.
- Writes predictions to `submission.csv` with columns `image_id`, `soil_type`.

---

## Part 2 — Code Details (`Part-2.ipynb`)

**Framework:** PyTorch / torchvision + scikit-learn

**1. Kaggle setup** — installs the `kaggle` CLI and configures `~/.kaggle/kaggle.json` credentials for data access.

**2. Paths** — reads from
`/kaggle/input/soil-classification-part-2/soil_competition-2025/` (`train/`, `test/`, `train_labels.csv`, `test_ids.csv`).

**3. Preprocessing** — single shared transform for train and test: `Resize(224, 224)` → `ToTensor()` → `Normalize(mean=[0.5]*3, std=[0.5]*3)` (scales pixel values to roughly `[-1, 1]`).

**4. Custom `SoilDataset`** — loads an image by `image_id`, converts to RGB, applies the transform, and returns `(image, image_id)`. `DataLoader` batch size: 32, no shuffling (order preserved for feature/ID alignment).

**5. Feature extraction (frozen backbone)**
- Loads **ResNet18** pretrained on ImageNet.
- Replaces the final classification layer with `nn.Identity()`, turning it into a **512-dim feature extractor** (set to `.eval()` mode — no fine-tuning).
- Runs all train and test images through the backbone (`torch.no_grad()`) to get feature vectors + their `image_id`s.

**6. Feature scaling** — features are standardized with `sklearn.preprocessing.StandardScaler` (fit on train features, applied to both train and test).

**7. One-Class SVM (novelty detection)**
- Since only "soil" images exist in the training set (no explicit negative/non-soil class), a `sklearn.svm.OneClassSVM` (`kernel='rbf'`, `gamma='scale'`, `nu=0.1`) is fit on the **soil-only training features** to learn the decision boundary of what a soil image "looks like" in feature space.
- On the test set, the SVM predicts `+1` (inlier → soil) or `-1` (outlier → not soil), which is converted to a binary label: `1 = soil`, `0 = not soil`.

**8. Submission** — writes `submission.csv` with columns `image_id`, `label` (0/1).

---
