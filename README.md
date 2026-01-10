
# DVIO: Robust Deep Visual-Inertial Odometry
A Monocular, Uncertainty-Aware VIO Framework for Challenging Environments

**

📌 Overview
This repository is a fork of the original DVIO project, significantly enhanced to improve robustness, adaptability, and data efficiency. While the original framework relied on stereo vision and standard Kalman Filtering, this implementation transitions to a Monocular setup using the KITTI Dataset and introduces a novel fusion backend to handle complex visual degradation.

Key improvements include a confidence scaling metric to quantify model uncertainty and extensive data augmentation (e.g., synthetic shadows) to ensure reliable performance in low-light and high-contrast environments.

🚀 Key Contributions & Features
1. Monocular Vision Transition
Original: Relied on Stereo Camera setups for depth and feature tracking.

My Contribution: Refactored the entire pipeline to operate with Monocular vision only. The system now effectively estimates depth and ego-motion using single-camera sequences from the KITTI Benchmark, reducing hardware requirements while maintaining trajectory accuracy.

2. Advanced Sensor Fusion Module
Original: Used a standard Kalman Filter (KF) for fusing visual and inertial data.

My Contribution: Replaced the KF with a [Insert Your Fusion Method Here]. This new backend allows for tighter coupling of visual features and IMU readings, reducing drift in scenarios where linear filters typically fail.

3. Confidence & Uncertainty Quantification
New Feature: Added a dynamic Confidence Scale output.

Instead of blindly outputting a pose, the model now provides a confidence score indicating when prediction quality degrades (e.g., in textureless areas). This allows the system to flag potential errors relative to the ground truth.

4. Robustness via Data Augmentation
New Feature: Enhanced the training pipeline with aggressive data augmentation.

Moved beyond basic grayscale datasets by synthetically injecting features such as dark shadows, severe lighting changes, and noise. This results in a DVIO model that is significantly more robust to real-world environmental fluctuations.

📊 Methodology
Architecture
The system processes raw monocular images and IMU streams through a dual-branch network:

Visual Encoder: Extracts high-level geometric features from the KITTI monocular sequences.

Inertial Encoder: Processes high-frequency IMU data.

Fusion Layer: The custom [Insert Method] fuses these modalities to regress 6-DoF pose and velocity.

Dataset & Augmentation
We utilize the KITTI Odometry Benchmark. To prevent overfitting to "perfect" lighting conditions, we apply:

Shadow Injection: Simulating high-contrast shadows to test feature tracking resilience.

Photometric Distortion: Random brightness/contrast adjustments.

📈 Results
Preliminary results showcase improved trajectory alignment in Sequence 00-10 of the KITTI dataset, specifically in segments with simulated lighting degradation.

(Add plots or trajectory comparisons here once available)

🛠️ Dependencies
Python 3.8+

PyTorch / TensorFlow

ROS (Noetic/Humble)

OpenCV

NumPy / Pandas

(Add specific libraries required by your new fusion method)

📜 Acknowledgements
This project is forked from the original DVIO repository. We thank the original authors for their foundational work.

[Link to Original Repo]

KITTI Dataset Team

Relevant Video Resource: For a broader understanding of deep learning approaches in this field, you might find this overview helpful: Deep Visual Inertial Odometry with Kalman Filter.

This video is relevant as it discusses the foundational concepts of Deep VIO and Kalman Filtering, which provides context for why you chose to replace the standard KF with your advanced fusion approach.

Youtube Overview: 
<a href="https://youtu.be/T8hH6Q6KIrc?si=aMZP8SQk5q0PdzRC" target="_blank">
  <img src="https://github.com/ElliotHYLee/Deep_Visual_Inertial_Odometry/blob/docker/yt.png" alt="Alt Text">
</a>


