# mouse-widefield-ripple-analysis
Python analysis of mouse wide-field glutamate imaging (iGluSnFR), hippocampal MUA, and EMG around awake ripples.
# Mouse Wide-Field Glutamate Imaging & Hippocampal Ripple Analysis

An independent Python data analysis project exploring neocortical glutamate dynamics (iGluSnFR), hippocampal CA1 multi-unit activity (MUA), and neck EMG around awake hippocampal sharp-wave ripples (SWRs) in mice.

## Data Source
This project uses the publicly available `iGluSnFR_Ras` dataset (Layer 2/3 excitatory neurons, Rasgrf2-dCre mice) from Prof. Majid Mohajerani's lab at McGill University.
- Dataset: Dryad Digital Repository (`doi:10.5061/dryad.8kprr4xrk`)
- Note: Raw `.mat` files (>100 MB) are excluded from this repository. Download `iGluSnFR_Ras.mat` from Dryad to run the notebooks locally.

## Key Results

### 1. Spatiotemporal Glutamate Dynamics Across 15 Neocortical Regions
Reproduces the widespread pre-ripple cortical inhibition followed by post-ripple activation across 15 neocortical regions (n = 865 ripples, Animal 1).

<img width="596" height="414" alt="heat_map" src="https://github.com/user-attachments/assets/adc00421-23fd-468a-a5e5-42032f02bf7b" />


### 2. Behavioral State Control (Low vs. High EMG)
Separating quiet and active states using neck EMG amplitude (median split) confirms that the pre-ripple inhibition and post-ripple rebound in the retrosplenial cortex (RSC) are not movement artifacts.

<img width="579" height="433" alt="RSC_low:high_EMG" src="https://github.com/user-attachments/assets/9bc0bd8c-b20b-4e7f-8924-55ee5c6cd1bf" />


### 3. Neocortical Functional Connectivity
15 × 15 Pearson correlation matrix illustrating high global synchronization across the dorsal neocortex during hippocampal ripples.

<img width="565" height="475" alt="EMG_pearsonr" src="https://github.com/user-attachments/assets/f3f04708-b68b-4984-b3e9-4c507c1659ef" />


## Notebooks Overview
1. `01_ripple_triggered_average.ipynb` — Loads MATLAB v7.3 (HDF5) data via `h5py`, computes ripple-triggered averages with SEM, and plots the 15-region heatmap.
2. `02_emg_state_and_connectivity.ipynb` — Performs EMG-based Boolean masking and computes the neocortical functional connectivity matrix.
3. `03_emg_spectral_filtering.ipynb` — Estimates Power Spectral Density (Welch's method) and applies a 4th-order zero-phase Butterworth bandpass filter (50–300 Hz).

## Requirements
Python 3.x, `h5py`, `numpy`, `scipy`, `matplotlib`
