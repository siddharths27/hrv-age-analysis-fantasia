# HRV Age Analysis — Fantasia ECG Dataset

A Heart Rate Variability (HRV) analysis pipeline comparing 
autonomic nervous system activity between young and elderly 
adults using the PhysioNet Fantasia dataset.

## Research Question
Does age significantly affect Heart Rate Variability as 
measured by time-domain HRV metrics?

## Dataset
PhysioNet Fantasia Database
- 20 healthy adults: 10 young (21–34 years) and 10 elderly (68–81 years)
- 2-hour ECG recordings during sleep
- Beat annotations in CSV format with time (ms) and type columns

## What I Built

### hrv.py — Custom HRV Analysis Module
Two core functions:

**calculate_HRV_metrics(file_in)**
Extracts 6 time-domain HRV metrics from raw ECG beat annotation files:

| Metric | Description | Unit |
|---|---|---|
| Mean NN | Average of all NN intervals | ms |
| Mean BPM | Mean heart rate | beats/min |
| SDNN | Standard deviation of NN intervals | ms |
| RMSSD | Root mean square of successive differences | ms |
| pNN20 | % of successive NN differences > 20ms | % |
| pNN50 | % of successive NN differences > 50ms | % |

**process_HRV_files(files_in, file_out)**
Batch processes all 20 recordings into a single results CSV.

## Statistical Analysis
Independent-samples t-tests comparing young vs elderly groups:

| Metric | p-value | Significance |
|---|---|---|
| Mean BPM | 0.433 | Not significant |
| RMSSD | 0.022 | * |
| SDNN | 0.003 | ** |
| pNN50 | <0.001 | *** |

## Key Findings
- Young adults show significantly higher HRV than elderly 
  across all parasympathetic metrics
- Mean heart rate does not differ significantly between groups
- Poincaré plots show visibly wider ellipses for young adults, 
  confirming higher short-term vagal variability
- Findings align with known age-related autonomic decline

## Tools
Python · NumPy · pandas · scipy · matplotlib

## References
- PhysioNet Fantasia Database — physionet.org/content/fantasia
- Umetani et al. (1998) — Age and gender differences in HRV
- Shaffer & Ginsberg (2017) — HRV norms and reference ranges
