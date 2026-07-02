<div align="justify">

# A Ventriculomegaly Feature Computational Framework for CT

This repository provides code to evaluate a set of eight ventriculomegaly features on non-contrast Computed Tomography (CT) scans. These features include the Evans indices (x,y,z), Callosal Angle (CA), normalized maximum third ventricle width (NMax-3VW), 
cerebrospinal fluid to brain volume ratio (CSF2BVR), the maximum eccentricity of lateral ventricles (MaxEccLV), and a proxy Splenial Angle (p-SA). 

## Model Availability Disclaimer
As this framework was originally developed using data from the Dept. of Veterans Affairs (VA), we are unable to publicly release the internal VA head CT scans due to patient privacy regulations and data security policies. However, we provide the complete
source code and a detailed step-by-step tutorial to enable researchers to extract the features on their own datasets.

## Data Requirements
This framework was evaluated on a structurally diverse set of 200+ non-contrast CT scans from patients with Normal Pressure Hydrocephalus (NPH), Alzheimer's Disease (AD), post-traumatic volume loss (PTVL), and headache (HC). Hyperparameters for the image processing 
pipelines were emperically derived and proved to work on this structurally diverse set. Since our scans only included chronic neurodegeneration, these parameters are expected to translate to datasets without acute findings such as significant midline shifts, bleeding,
or mass effects. Anterior commissure (AC) and posterior commissure (PC) coordinates are required to guide ROI placement and slice selection for computing these features. Note also that the input volumes required for these pipelines are assumed to be tilt corrected 
such that the AC-PC line is horizontal and the midline is vertical (we provide a notebook to perform this correction using the AC-PC, and midline coordinates).

We direct researchers to utilize our AC-PC prediction framework for head CT (https://github.com/samadanilab/AC-PC-Landmark-Prediction), which can automatically predict the locations of the AC and PC landmarks. Since this framework does not include midline localization, 
a set of 20 manually localized mid-sagittal-plane points are required to be input to achieve midline alignment (takes under 1 minute per scan). 
3D-Slicer's AC-PC Transform module is recommended to align the volumes using our automatically predicted AC and PC landmarks, and the midline points. 

## System Requirements
Our evaluations were on a Windows machine () with the following specifications:\
CPU: Intel(R) Core(TM) i9-10850K CPU @ 3.60GHz 20M Cache\
Cores: 10 Cores / 20 Threads\
Memory: 32GB\

## Illustration of the computed ventriculomegaly features on representative CT scans of patients with NPH, AD, HC, and PTVL. 
![Ventriculomegaly-Feature-Computation](assets/ven_features_illustration.jpg)

### Data Setup
**This repository does not contain head CT data**. Before running the pipeline, make a copy of config.template.json, rename it to config.json, and update the paths to point to your local dataset.

## Citation
If you find this code useful, please cite our work:
Kadaba Sridhar S, Kuang R, Dysterheft Robb J, Samadani U. A ventriculomegaly feature computational pipeline to improve the screening of normal pressure hydrocephalus on CT. J Neurosurg. 2024 Mar 8;141(3):822-832. doi: 10.3171/2023.12.JNS231780. PMID: 38457801.

## Acknowledgments
This work utilized **3D Slicer** (https://www.slicer.org/) for image preprocessing and head tilt correction (AC-PC and midline alignment). If you use this code for your research, please also cite 3D Slicer in your work [2].

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

