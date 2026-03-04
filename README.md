# MLy Pipeline Bias Analysis

This repository contains a Jupyter notebook for analysing detection bias in the 
MLy gravitational-wave burst detection pipeline across a range of frequencies using 
controlled sine-Gaussian injections.

## Overview

The notebook runs the `Validator.accuracy()` function from the MLy pipeline across 
a user-defined frequency range and SNR sweep, and generates a set of visualisations 
to characterise detection efficiency and identify frequency-selective bias in the 
two MLy models.

## Contents
```
Bias identification for MLy-Visualiation methods.ipynb   # Main notebook
README.md             # This file
```

## Requirements

This notebook requires the MLy pipeline to be installed and accessible. See the 
[MLy repository](https://github.com/VasSkliris/mly) for installation instructions.

Other dependencies:
- numpy
- matplotlib
- scipy

## Usage

1. Load your trained MLy models and set the path to your injection files
2. Define your frequency range and SNR values
3. Run the notebook top to bottom

The notebook will run the validator, store results, and generate all plots 
automatically.

## Visualisations

The following plots are generated:

- **Efficiency heatmap** — detection efficiency as a function of frequency and SNR 
  for Model 1, Model 2, and the combined score
- **Efficiency vs SNR curves** — per-frequency detection curves showing onset and 
  saturation
- **SNR at 50% and 90% efficiency** — detection threshold per frequency for both 
  models
- **Efficiency vs frequency at fixed SNRs** — sensitivity across the band at SNR 
  values of 10, 15, 20, 25, and 30
- **Bias bar chart** — average efficiency per frequency expressed as deviation from 
  the mean, with underperforming frequencies flagged

## Parameters

| Parameter | Description |
|---|---|
| `frequencies` | List of frequencies to sweep over (Hz) |
| `snr_values` | Array of SNR values to test |
| `N_PER_FREQ` | Number of waveforms per frequency for sky projection averaging |
| `threshold` | Efficiency threshold for SNR extraction (default 0.5) |

## Notes

- Frequencies above 470 Hz approach the Nyquist limit of 512 Hz and should be 
  interpreted with caution
- It is recommended to use N_PER_FREQ >= 50 to average over random sky projections 
  and avoid projection artefacts being misidentified as model blind spots
- Results are saved as a pickle file for reuse without rerunning the full injection

## References

Skliris, V., Norman, M. R. K., and Sutton, P. J. (2024). Toward real-time detection 
of unmodeled gravitational wave transients using convolutional neural networks. 
*Phys. Rev. D*, 110, 104034. https://doi.org/10.1103/PhysRevD.110.104034
