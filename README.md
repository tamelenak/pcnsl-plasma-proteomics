# Plasma Proteomics for Predictive and Prognostic Stratification in Newly Diagnosed PCNSL

Analysis code for the study of plasma proteomic biomarkers in primary central nervous
system lymphoma (PCNSL). The work uses Olink Proximity Extension Assay (PEA) plasma
proteomics from patients in the French LOC network, integrated with tumour
transcriptomics (RNA-seq) in patient subsets, to identify immune signatures predictive of treatment response and survival.

## Study design

- **Cohort:** newly diagnosed PCNSL patients from the French LOC network.
  - Training: enrolled Jan 2016 – Jun 2019 (two technical outliers, `patient_id` 73 and 86, excluded in-notebook).
  - Validation: enrolled Jul 2019 – Dec 2022.
- **Platform:** Olink PEA, Reveal panel (1007 proteins after QC).
- **Endpoints:** overall survival (OS), progression-free survival (PFS), and binary
  treatment-response / survival-landmark endpoints.

## Repository contents

```
├── main_analysis.ipynb              # Main figures: consensus clustering, immune-signature KM,
│                                    #   Cox forest, C-index benchmark, binary elastic-net benchmark,
│                                    #   and supplementary sensitivity analyses
├── transcriptomics_integration.ipynb # Paired tumour RNA (VST) vs plasma protein (NPX) discordance
├── requirements.txt                 # Pinned Python dependencies
└── README.md
```

**Proteomics file:** ~172 rows (164 patients + 8 replicates) and 1007 protein NPX columns
plus clinical metadata (`patient_id`, `sex_completed`, `age_years`, `cohort`,
`Karnofsky_status`, `estimated_OS_months`, `estimated_OS_event`, `estimated_PFS_months`,
`estimated_PFS_event`). 

## Immune signatures

Four pre-specified plasma immune signatures (scored as the mean of constituent NPX values):

- **IFN/Chemokine:** CXCL9, CXCL10, IFNG, CCL19, CCL20, CCL3, CCL4
- **Checkpoint/Cytokine:** IL10, IL6, PDCD1, PDCD1LG2, LAG3, CD86, TNF
- **Innate/Inflammatory:** IL1B, IL6, TNF, CCL20, CCL3, CCL4, FASLG
- **Integrated Immune:** union of the above (17 proteins, including TNFRSF13C)

## Setup

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

## Data and Code Availability

This code is released to support reproducibility of the analyses reported in the
manuscript. Anonymized patient-level proteomics data are availabel on Zenodo: [TBD].
