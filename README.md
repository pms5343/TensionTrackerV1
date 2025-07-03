# TensionTrackerV1
Estimate wire tension via SAM2-based ROI, CoTracker2-based strain estimation, and edge-based lay angle

## System Requirements
All experiments were conducted under the following hardware and software configuration:

### Hardware Environment
* Workstation: Dell Precision 7920 Rack
* CPU: Intel Xeon Silver 4210R (10 cores, 20 threads, 2.4–3.2 GHz)
* Memory: 128 GB DDR4-3200 ECC
* GPU: NVIDIA RTX A6000 (48 GB GDDR6 ECC)
* Storage: 1 TB NVMe SSD
* Operating System: Ubuntu 20.04 LTS
### Software Environment
* Python: 3.10.13
* CUDA : 12.5

## Preparation

* Clone or download the code package from this repository.
* Set the working directory:
```python
MainFolder = "/your/custom/path"
```

## 📥 Download Pre-trained Models and Fine Tuning

The following checkpoints are required. Please download and place each file in the specified directory.

🔹 SAM2 (Segment Anything Model V2)
* Checkpoint:   sam2.1_hiera_large.pt
* Destination:  sam2_repo/checkpoints/
* Download:     https://github.com/facebookresearch/sam2
* Config Base: sam2.1_hiera_l.yaml
- `multimask_output_in_sam = False`  
  → Since only a single-object segmentation is required, multi-mask output is disabled.

- `num_maskmem = 3`  
  → Reduced from the default (7) to improve memory efficiency, as the strand shape does not change drastically over time.

- `image_size = 1920`  
  → Adjusted to match the input video resolution (1080×1920); the default was 1024.

🔹 CoTracker
* Checkpoint:   cotracker2.pth
* Destination:  co-tracker/cotracker/checkpoints/
* Download:     https://github.com/facebookresearch/co-tracker/tree/8d364031971f6b3efec945dd15c468a183e58212
- `grid_size = 200`
- `pad_value = 5`  

🔹 Edge Detection
- `LDC Threshold = 0.7`  
  → All mask values below 0.7 are considered non-edge (i.e., discarded during boundary detection).
- `HoughLineP Threshold = 100`  
  → Threshold used in Probabilistic Hough Transform to detect lines from the extracted edges.


## Results
<p align="center">
  <img src="https://github.com/user-attachments/assets/997fcb52-82d2-4d0d-97dc-8cfabec4c8ef" width="300" height="550"/>
  <img src="https://github.com/user-attachments/assets/ba59af41-b9fe-4bae-bed6-d0aaf565afa5" width="300" height="550"/>
</p>

# Citation  
The citation information will be available soon.

## Contributors
<p>
  <small>Ph.D. Candidate</small>
  <strong>Dongyoung Ko</strong>
  <a href="https://sites.google.com/view/skkuscit" target="_blank">
    <img src="https://github.com/pms5343/Tension_aware_Wire_Tracker/raw/main/logo/skku.svg" height="20" alt="SKKU Logo"/>
  </a>
  <a href="https://scholar.google.com/citations?user=uJ5Ot9kAAAAJ&hl=en" target="_blank">
    <img src="https://img.shields.io/badge/-4285F4?style=flat&logo=googlescholar&logoColor=white" alt="Google Scholar"/>
  </a>
  <a href="https://github.com/ehddud3555-skku" target="_blank">
    <img src="https://img.shields.io/badge/-000000?style=flat&logo=github&logoColor=white" alt="GitHub"/>
  </a>
</p>

<p>
  <small>Professor</small>
  <strong>Minsoo Park</strong>
  <a href="https://sites.google.com/view/iisc-lab" target="_blank">
    <img src="https://github.com/pms5343/Tension_aware_Wire_Tracker/raw/main/logo/GWNU.svg" height="20" alt="GWNU Logo"/>
  </a>
  <a href="https://scholar.google.com/citations?user=6dCUM5oAAAAJ&hl=En">
    <img src="https://img.shields.io/badge/-4285F4?style=flat&logo=googlescholar&logoColor=white" alt="Google Scholar"/>
  </a>
  <a href="https://github.com/pms5343">
    <img src="https://img.shields.io/badge/-000000?style=flat&logo=github&logoColor=white" alt="GitHub"/>
  </a>
</p>


<p>
  <small>Professor</small>
  <strong>Seunghee Park</strong>
  <a href="https://sites.google.com/view/skkuscit" target="_blank">
    <img src="https://github.com/pms5343/Tension_aware_Wire_Tracker/raw/main/logo/skku.svg" height="20" alt="SKKU Logo"/>
  </a>
  <a href="https://scholar.google.com/citations?user=uJ5Ot9kAAAAJ&hl=en" target="_blank">
    <img src="https://img.shields.io/badge/-4285F4?style=flat&logo=googlescholar&logoColor=white" alt="Google Scholar"/>
  </a>
  <a href="https://github.com/ehddud3555-skku" target="_blank">
    <img src="https://img.shields.io/badge/-000000?style=flat&logo=github&logoColor=white" alt="GitHub"/>
  </a>
</p>
