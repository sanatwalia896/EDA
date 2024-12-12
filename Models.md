# README

## 1. Anti-Spoofing Model

The **Anti-Spoofing** model is a lightweight, real-time solution for detecting spoofed face images or videos (e.g., photos, videos, or 3D masks). It works seamlessly without user interaction and integrates Fourier Transform (FT) analysis with convolutional networks to distinguish real faces from spoofed ones. Designed to be highly efficient for all types of devices with model size of 1.9 mb and in onnx format ensuring cross platform compatibility .

### Key Features:
- **Real-Time Performance**: Delivers fast image processing with a **97.8% True Positive Rate (TPR)** and a **0.5% False Positive Rate (FPR)**, making it ideal for devices with limited computational power.
- **Compact and Lightweight**: The model is optimized for efficiency, with a size of only **5MB to 7MB**. This is achieved through techniques such as model pruning, depthwise separable convolutions, and optimized training methods.
- **Fourier Transform Integration**: Incorporates a Fourier Transform auxiliary branch to extract frequency-domain features, enhancing the model's ability to detect spoofing without increasing the model size.
- **Multi-Stage Learning**: The model uses two main branches to process the input:
  - **Frequency Domain Branch**: Captures frequency-domain features via Fourier Transform.
  - **Spatial Domain Branch**: Processes image data using a convolutional network for final predictions.
**Edge & Browser Compatibility**: This model can run efficiently on edge devices and in any modern browser, thanks to its small size of 1.9mb and use of the ONNX format.

### Architecture Overview:
- **Input Image**: (Size: 80x80)
  - Fourier Transform captures frequency-domain features.
  - Image normalization and resizing are performed.
- **Feature Extraction**: Convolutional layers extract both spatial and frequency-domain features.
- **Loss Functions**:
  - **FT Loss**: For frequency-domain supervision.
  - **Softmax Loss**: For binary classification (real vs. fake).
# Fourier Transform Pipeline with MiniFASNet

# Face Antispoofing Model Architecture

```
mermaid
graph TD
    A[Input Image (1x3x80x80)] --> B[Fourier Transform]
    B --> C[Normalization]
    C --> D[Resize (1x1x10x10)]
    D --> E[FT Loss]
    D --> F[FT Generator]
    F --> G[Feature Map (1x128x10x10)]
    G --> H[Flatten (1x512)]
    H --> I[Softmax Loss]

    subgraph MiniFASNet
        F --> J[Conv3x3 (128)]
        J --> K[Conv3x3 (64)]
        K --> L[Conv3x3 (32)]
        L --> G
    end
```

## Model Benchmarks
### antispoofing_bin_1.5_128.onnx
- Execution Provider: **CPExecutionProvider**
- **Average Inference Time**: 0.002726 seconds
- **FPS (Frames Per Second)**: 366.81
- **Total Inference Time for 100 runs**: 0.27 seconds
- **Computer Memory Usage Before**: 62.66 MB
- **Computer Memory Usage After**: 62.73 MB
- **Memory Usage by Model during Inference**: 0.07 MB



### antispoofing_bin_1.5_128.onnx
- Execution Provider: **CPExecutionProvider**
- **Average Inference Time**: 0.002726 seconds
- **FPS (Frames Per Second)**: 366.81
- **Total Inference Time for 100 runs**: 0.27 seconds
- **Computer Memory Usage Before**: 62.66 MB
- **Computer Memory Usage After**: 62.73 MB
- **Memory Usage by Model during Inference**: 0.07 MB
- **Model Output Shapes**: [(1, 2)]


For more details, visit the [Silent-Face-Anti-Spoofing GitHub Repository](#) , [https://github.com/hairymax/Face-AntiSpoofing](#)..


---

## 2. YOLOv7 Lite for Face Detection

**YOLOv7 Lite** is a streamlined version of the well-known YOLOv7 architecture, specifically designed for fast and efficient face detection with a smaller computational footprint. It is ideal for real-time face detection applications, where low resource consumption and fast processing are crucial.

### Key Features:
- **Optimized for Speed**: YOLOv7 Lite is engineered for real-time face detection, offering significant reductions in computational overhead compared to the original YOLOv7, making it suitable for devices with limited resources such as smartphones or embedded systems.
- **Efficient Architecture**: With fewer parameters and lightweight components, YOLOv7 Lite strikes a balance between speed and accuracy, excelling in face detection tasks.
- **High Detection Accuracy**: Despite its smaller size, YOLOv7 Lite delivers impressive face detection accuracy and performs well in various environments, including high-density scenes.
- **Mobile Deployment**: Perfect for mobile and edge devices like Raspberry Pi, supporting both **CPU and GPU inference**.

### Architecture Overview:
- **Backbone**: A modified YOLOv7 backbone, optimized to reduce complexity while maintaining effective detection capabilities.
- **Detection Head**: A dedicated head designed specifically for face detection, fine-tuned for optimal performance.
- **Post-Processing**: Utilizes Non-Maximum Suppression (NMS) to eliminate redundant detections and improve face localization.

### Advantages:
- **Real-Time Detection**: Capable of processing images swiftly, making it suitable for applications like surveillance, face recognition systems, and user interaction systems.
- **Resource Efficiency**: Small in size and computationally efficient, YOLOv7 Lite is an excellent choice for face detection on mobile and embedded platforms.

## Model Benchmarks
### YOLO-7lite.onnx
- Execution Provider: **CPExecutionProvider**
- **Average Inference Time**: 0.036573 seconds
- **FPS (Frames Per Second)**: 27.34
- **Total Inference Time for 100 runs**: 3.66 seconds
- **Computer Memory Usage Before**: 129.72 MBMemory
- **Computer Memory Usage After**: 129.92 MB
- **Memory Usage by Model during Inference**: 0.02 MB


For further details, visit the [YOLOv7 Lite Face Detection GitHub Repository](#).

