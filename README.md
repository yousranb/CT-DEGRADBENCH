# CT-DEGRADBENCH  
**A benchmark of controlled CT degradations (noise, blur, sparse-view aliasing)**

This repository presents **CT slice sequences degraded in a controlled and physically-inspired way**, 
designed for **visual analysis, robustness evaluation, and learning-based reconstruction / denoising tasks**.

All degradations are exported as **single GIFs** composed of **145 consecutive slices**, where degradation parameters
change **block-wise along the slice axis**.

---

## 📌 Degradations Overview

| Degradation | Description | Preview |
|------------|-------------|---------|
| **Noise Synthesis** | Projection-domain Mixed Gaussian-Poisson noise with residual amplification | <img src="gifs/ct_noise_blocks.gif" width="300"/> |
| **Loss of sharpness** | Detector blur applied in sinogram domain | <img src="gifs/ct_blur_blocks.gif" width="300"/> |
| **Sparse-view aliasing Effect** | Sparse View CT | <img src="gifs/gif_aliasing_blocks.gif" width="300"/> |

---

## 🔬 Noise Degradation (γ blocks)

- Poisson noise injected in projection domain
- Zero-mean residual boosted to avoid streak artifacts
- Parameters:
γ = (1, 2, 2.5, 4)
Block sizes = (37, 37, 37, 34)

Each block corresponds to a different noise intensity.

---

## 🔎 Loss of Sharpness (σ blocks)

- Sinogram-domain detector blur (Gaussian)
- Physically interpretable loss of spatial resolution
- Example configuration:

σ_det = (0.0, 0.8, 1.0, 1.5, 2.5)
Block sizes = (29 × 5)

---

## 🧩 Sparse-View Aliasing (View blocks)

- Full-view sinogram computed once
- Sub-sampled angular views reconstructed
- Parameters:
n_views = (180, 90, 60, 45)
Block sizes = (37, 37, 37, 34

Produces characteristic aliasing artifacts.

---

## ⚙️ Technical Details

- Image domain: Hounsfield Units (HU)
- Linear attenuation: μ = μ_water (1 + HU / 1000)
- μ_water = 0.02 cm⁻¹
- Radon angles: 360 views over [0°, 180°)
- Reconstruction: Filtered Backprojection (ramp)
- Display window: [-300, +300] HU

---

## 📁 Code

Scripts used to generate the degradations are available in:


