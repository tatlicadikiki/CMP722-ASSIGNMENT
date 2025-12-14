# CMP722-ASSIGNMENT

# Self-Supervised Learning vs. Fine-Tuning: A Comparative Analysis on Satellite Imagery (EuroSAT)

This repository contains the implementation and analysis for the **CMP722 - Advanced Computer Vision** assignment. The project investigates the efficacy of representation learning techniques in the domain of remote sensing, specifically comparing **Supervised Fine-Tuning**, **Training from Scratch**, and **Self-Supervised Learning (SimCLR)**.

## Objective
To explore how representation learning and transfer learning can improve model performance on domain-specific datasets (Satellite Imagery) compared to training from scratch, with a focus on label efficiency and convergence speed.

## Dataset: EuroSAT (RGB)
We utilized the **EuroSAT** dataset, which consists of Sentinel-2 satellite images.
* **Total Images:** 27,000
* **Classes (10):** Annual Crop, Forest, Herbaceous Vegetation, Highway, Industrial, Pasture, Permanent Crop, Residential, River, Sea/Lake.
* **Split Strategy:** To prevent data leakage and ensure robust evaluation, the data was split into **70% Train**, **15% Validation**, and **15% Test**.

## Methodologies Implemented

All experiments utilize a **ResNet-18** backbone.

1.  **Baseline (Training from Scratch):**
    * Standard supervised learning with random weight initialization.
    * Serves as a reference point for learning without prior knowledge.
2.  **Transfer Learning (Fine-Tuning):**
    * ResNet-18 pretrained on **ImageNet**.
    * The final fully connected layer is modified for 10 classes.
    * Demonstrates the transferability of features from natural images to satellite data.
3.  **Self-Supervised Learning (SimCLR):**
    * **Pre-training:** Contrastive learning using NT-Xent loss on unlabeled data (30 Epochs).
    * **Augmentations:** RandomResizedCrop, ColorJitter, RandomGrayscale.
    * **Linear Evaluation:** Freezing the encoder and training a linear classifier on top.

**Note:** An **Early Stopping** mechanism (Patience=5) based on Validation Loss was implemented for all experiments to prevent overfitting.
