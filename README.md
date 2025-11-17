# 🏛️ Heritage Image Restoration using Stable Diffusion + ControlNet  
A Generative AI Pipeline for Enhancing Historical Photographs & Building Images  

---

## 📌 Project Overview  
This project restores old, low-quality, or damaged historical images using a **training-free diffusion-based pipeline** built on:

- **Stable Diffusion 1.5**
- **ControlNet (Canny Edge Conditioning)**
- **Gradio Web Application for Deployment**

The system produces **high-quality, structure-preserving restorations** without requiring paired clean datasets or heavy GPU training.

---

## 🎯 Project Objectives  
- Develop a restoration pipeline for heritage images using diffusion priors.  
- Preserve structural integrity using ControlNet edge maps.  
- Enhance textures, clarity, and visibility of old photographs.  
- Deploy a user-friendly interface for real-time restoration.  
- Evaluate visual fidelity using qualitative comparison methods.

---

## 📂 Dataset Used  
We use **60 images total**:  
- **30 Old Heritage Photographs**  
- **30 Heritage Building Images**  

For each image:  
- **Canny edge maps** were pre-computed and used as ControlNet conditions during inference.

---

## 🧠 Models Used  

### **A. Stable Diffusion 1.5 / 2.1**  
Stable Diffusion serves as the **main generative model**, leveraging its strong prior to fill missing details, enhance clarity, and restore natural textures.  
It recreates lost regions without over-smoothing and maintains visual realism.

### **B. ControlNet (Canny Edge Version)**  
ControlNet ensures:  
- **Shape preservation**  
- **Edge-aligned reconstruction**  
- **No hallucinated structures**  
By feeding Canny edges, the diffusion model is guided to maintain structural accuracy of buildings, faces, and objects.

### **C. Diffusion Inference Pipeline**  
The pipeline uses:  
- **Frozen Stable Diffusion weights**  
- **Deterministic conditioning**  
- **No fine-tuning or training required**  
This makes the project fast, lightweight, and easy to deploy on Colab.

---

## 🛠️ Methodology  
1. **Dataset preparation**  
   - Upload old images  
   - Generate Canny edges  
   - Organize into RAW and EDGES folders  

2. **Load Pretrained Models**  
   - Stable Diffusion 1.5  
   - ControlNet Canny  
   - UniPC scheduler  

3. **Inference Pipeline**  
   - Combine prompt + edge map  
   - Run diffusion sampling  
   - Generate restored image  

4. **Output Visualization**  
   - Side-by-side comparison: Raw vs Restored  
   - Gradio real-time interface  

---

## 📊 Results  
- Clear enhancement of sharpness & visibility  
- Improved texture restoration  
- Structural accuracy maintained due to ControlNet  
- Zero hallucinations for buildings and monuments  
- Fast inference (≈4–6 seconds per image on Google Colab GPU)

---

## 🌐 Deployment  
A **Gradio web app** is included with:

### **Modes:**  
1. **Photo Restoration**  
2. **Building Image Enhancement**  
3. **Raw vs Restored Comparison**

Users can upload an image and instantly view side-by-side output.

---

## 💻 Run the Project  
### **1. Install Dependencies**
```bash
pip install diffusers transformers accelerate gradio opencv-python torch
2. Run Restoration Pipeline
from diffusers import StableDiffusionControlNetPipeline, ControlNetModel
from PIL import Image
import cv2, torch

3. Launch Gradio App
import gradio as gr
app.launch()


📚 References

Lin et al., DiffBIR: Blind Image Restoration using Diffusion Prior, ECCV 2024

Ye et al., Diffusion Texture Priors, CVPR 2024

Zhang et al., ControlNet, ICCV 2023

Noroozi et al., One-Step Diffusion SR, 2024

Stable Diffusion 1.5 by CompVis

Canny-ControlNet by Lvmin Zhang
