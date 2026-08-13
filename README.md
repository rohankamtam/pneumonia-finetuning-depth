# Impact of Fine-Tuning Depth on Model Performance and Explainability in Transfer Learning-Based Pneumonia Detection

[![View Site](https://img.shields.io/badge/site-live-5fd8e8?style=flat-square)](https://rohankamtam.github.io/pneumonia-finetuning-depth/)
[![Paper](https://img.shields.io/badge/paper-IJERT-e2624f?style=flat-square)](./paper/IJERT_pneumonia_finetuning_depth.pdf)
[![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-blue?style=flat-square)](https://creativecommons.org/licenses/by/4.0/)

Investigating how the depth of fine-tuning in ResNet50 transfer learning affects both
classification accuracy **and** spatial explainability (Grad-CAM, SHAP, IOLAR) in
chest X-ray pneumonia detection.

**🔗 Live project page:** `https://rohankamtam.github.io/pneumonia-finetuning-depth/` (set up in Step 6 below)

## Key finding

Partial fine-tuning (unfreezing only the final convolutional block) achieves the best
balance of accuracy and explainability. Pushing to full fine-tuning gains only 2.9%
more accuracy while explainability collapses — IOLAR drops from 0.91 to 0.19 on
pneumonia images, with both Grad-CAM and SHAP shifting attention to image borders
instead of lung tissue (p < 0.001, Cohen's d ≈ 1.2), indicating shortcut learning.

## Models compared

| Model | Strategy                    | Accuracy | N. Recall | P. Recall | AUC   |
|-------|------------------------------|----------|-----------|-----------|-------|
| A     | Frozen backbone               | 80.0%    | 53%       | 96%       | —     |
| B     | Partial fine-tuning (conv5)   | 86.4%    | 67%       | 98%       | 0.960 |
| C     | Full fine-tuning              | 89.3%    | 77%       | 96%       | 0.961 |

## Repository structure

```
.
├── docs/               # GitHub Pages site (project landing page)
│   └── index.html
├── notebooks/          # Training + explainability pipeline
│   └── pneumonia_finetune_depth.ipynb
├── paper/              # Published IJERT paper
│   └── IJERT_pneumonia_finetuning_depth.pdf
├── requirements.txt
└── README.md
```

## Running the notebook

```bash
pip install -r requirements.txt
jupyter notebook notebooks/pneumonia_finetune_depth.ipynb
```

Or open it directly in [Google Colab](https://colab.research.google.com/).

## Team

| Name | Department |
|------|------------|
| Ch. Bala Subramanyam | (Guide)CSE |
| Rohan Kamtam | CSE |
| Kamalesh Choudhary | CSE |
| G. Pavan | CSE |


Dept. of Computer Science and Engineering, Vardhaman College of Engineering, Hyderabad, India.

## Citation

If you use this work, please cite:

```
R. Kamtam, K. Choudhary, G. Pavan, Ch. B. Subramanyam,
"Impact of Fine-Tuning Depth on Model Performance and Explainability in Transfer
Learning-Based Pneumonia Detection," International Journal of Engineering
Research & Technology (IJERT), Vol. 15, Issue 04, April 2026.
```

## License

This project is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/),
consistent with the paper's publication license.
