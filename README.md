# Mechanistic Interpretability of Nuclear Mass Models

This repository contains the code used for the interpretability analysis in  
**[*The DNA of Nuclear Models: How AI Predicts Nuclear Masses*](https://arxiv.org/abs/2508.08370)**.

The goal of this project is to
understand **what the trained neural network learns** when predicting nuclear
binding energies from proton (Z) and neutron (N) numbers, and how this
information is encoded in its internal representations.

---

## Overview

The model learns embeddings for proton number (Z) and neutron number (N) and
uses these embeddings to predict nuclear binding energies. Despite being fully
data-driven, the learned representations exhibit strong low-dimensional
structure, including spiral / helical geometry and hierarchical organization
that mirrors well-known features of nuclear physics.

This repository focuses on:
- Training embedding-based nuclear mass models
- Extracting and analyzing learned representations
- Tracking embedding evolution during training
- Fitting low-dimensional geometric structures (e.g. helices) to embeddings
- Studying how embedding geometry affects physical predictions

---

## Repository structure

```text
NuCLR_DNA/
├── lib/
│   ├── model.py              # Neural network architecture and embeddings
│   ├── utils.py              # Shared utilities
│   └── symbolic_model.py     # Reference symbolic models (BW, WS4, etc.)
├── scripts/
│   ├── exps/                 # Experiment-specific configs
│   ├── multiruns.py          # Launch multiple runs (seeds / configs)
│   ├── pipeline.py           # High-level training + plotting entry point
│   ├── plot.py               # Standalone plotting utilities
│   └── run_pysr.py           # Symbolic regression with PySR
├── notebooks/
│   └── training.ipynb        # Training loop with embedding snapshots
├── experiments/
│   └── <experiment_name>/    # Saved models, PCA snapshots, plots
├── data/
│   └── ...                   # Datasets of nuclear observables
├── data.py                   # Dataset loading & preprocessing
├── train.py                  # Core training loop
├── symbolic_regression.py    # Post-hoc symbolic fits
├── requirements.txt
└── README.md


---

## Installation

Install the required Python dependencies with:

    pip install -r requirements.txt

GPU access is recommended for training and large-scale analysis.

---

## Training

The basic implementation of the training procedure used in the paper is provided
as a Jupyter notebook in the `notebooks/` directory. This notebook is intended to
be the most readable and self-contained entry point for understanding the model,
the data, and the training setup.

Models can also be trained using the pipeline script:

    python -m scripts.pipeline --exp <experiment_name> --train

Running the script as a Python module ensures that paths are set correctly and
that the `lib/` directory can be imported. Training outputs are stored in:

    experiments/<experiment_name>/

The `scripts/pipeline.py` interface is a **beta orchestration layer**, primarily
intended for large-scale or automated experiment management. It is not required
to reproduce the core results presented in the paper and may evolve over time.


## Scope and limitations

- This repository is intended for **analysis and reproducibility**, not
  large-scale optimization for mutli-task learning.

---

## Citation

If you use this code, please cite:

@article{Richardson:2025dze,
    author = "Richardson, Kate A. and Trifinopoulos, Sokratis and Williams, Mike",
    title = "{The DNA of nuclear models: How AI predicts nuclear masses}",
    eprint = "2508.08370",
    archivePrefix = "arXiv",
    primaryClass = "nucl-th",
    reportNumber = "CERN-TH-2025-153",
    month = "8",
    year = "2025"
}
