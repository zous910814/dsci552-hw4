# DSCI 552 — Homework 4

**Name:** Chihwei Huang
**USC ID:** 9265220160

Time series classification on the AReM (Activity Recognition system based on Multisensor data
fusion) dataset: time-domain feature extraction, binary classification of *bending* vs. the
other activities with logistic regression and L1-penalized logistic regression, and multi-class
classification of all activities, plus the ISLR exercises 4.8.3 and 4.8.7.

## Contents

```
.
├── README.md
├── requirements.txt
├── data
│   └── AReM
│       ├── bending1/ bending2/ cycling/ lying/ sitting/ standing/ walking/
│       ├── bendingType.pdf
│       └── sensorsPlacement.pdf
└── notebook
    └── Time Series Classification.ipynb
```

All answers — code, plots and the written discussion — are in
`notebook/Time Series Classification.ipynb`. Each question is introduced by a markdown cell
labelled with its number in the assignment (1(c)iii, 2(a)vii, and so on).

## Running

```bash
python -m venv venv
venv/Scripts/activate          # Windows;  source venv/bin/activate on macOS/Linux
pip install -r requirements.txt
jupyter notebook "notebook/Time Series Classification.ipynb"
```

Then use **Cell → Run All**. The notebook loads the data through the relative path
`../data/AReM`, so it must be run from the `notebook/` directory (which is where Jupyter puts
the working directory by default). A full run takes a few minutes, most of it spent on the
cross-validation sweeps over the 20 values of *l*.

## Notes on the data

Three files need minor cleaning, which the loader in the notebook handles automatically:

* `bending2/dataset4.csv` — fields are separated by spaces instead of commas.
* `cycling/dataset9.csv`, `cycling/dataset14.csv` — the last row ends with a trailing comma.
* `sitting/dataset8.csv` — one sample is missing (`t = 13500`), so the file has 479 rows.

Randomness (the bootstrap, the cross-validation folds and the case-control subsample) is seeded
with `RANDOM_STATE = 42`, so a re-run reproduces every number in the notebook.
