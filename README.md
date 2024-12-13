# FaceSwap: Seamless Face Replacement Tool
This Python project performs face swapping between two images. It uses facial landmarks, triangle-based transformations, and seamless blending to ensure realistic results.

## Features
- **Facial Landmark Detection**: Accurately detects 68 facial landmarks using dlib's pre-trained model.
- **Triangle Warping**: Divides the face into triangles for precise transformation and warping.
- **Seamless Blending**: Ensures the swapped face integrates smoothly into the target image.
- **Customizable Inputs**: Allows users to select source and target images.

## Requirements
To run this project, you need the following Python packages installed:

- opencv-python (cv2)
- numpy
- Pillow
- dlib

Install these dependencies using pip:

`pip install opencv-python numpy pillow dlib`

You also need to download the pre-trained dlib model for facial landmark detection:

[Download shape_predictor_68_face_landmarks.dat](https://drive.google.com/file/d/1Fh8-EaXcAFHIKGV8acppiabwHQHApQlF/view?usp=sharing)

# How It Works

## 1. Detect Facial Landmarks
The project uses a pre-trained dlib model to detect 68 key points on the face (eyes, nose, mouth, jawline, etc.).
These landmarks form the foundation for triangle-based transformations.

## 2. Divide Face into Triangles
The face is divided into multiple triangles using Delaunay triangulation.
Each triangle is mapped and warped from the source face to the target face.

## 3. Apply Seamless Cloning
Once all triangles are transferred, the face is blended seamlessly onto the target image using OpenCV's `cv2.seamlessClone` function.

# How to Run
1. Clone the repository and navigate to the project folder.
2. Download the [shape_predictor_68_face_landmarks.dat](https://drive.google.com/file/d/1Fh8-EaXcAFHIKGV8acppiabwHQHApQlF/view?usp=sharing) model and place it in the project directory.
3. Run the script:

    ```bash
    python FaceSwap.py
    ```

The program will prompt you to:
- Provide the path to the source image (face to transfer).
- Provide the path to the target image (face to replace).

The swapped face will be displayed as the output.

# Input Details
- **Source Image**: The image containing the face you want to transfer.
- **Target Image**: The image where the face will be replaced.

# Code Overview

## Main Functions

### `extract_index_nparray`
- **Description**: Extracts the first index from a numpy array. Used for identifying triangle points.
- **Parameters**:
    - `nparray`: Input numpy array.

### `detect_landmarks`
- **Description**: Detects facial landmarks using dlib's pre-trained model.
- **Parameters**:
    - `image_gray`: Grayscale image for landmark detection.

### `warp_triangle`
- **Description**: Warps a triangle from the source face to the corresponding position in the target face.
- **Parameters**:
    - `src_triangle`: Triangle points from the source face.
    - `dst_triangle`: Corresponding triangle points in the target face.

### `seamless_blend`
- **Description**: Blends the swapped face seamlessly onto the target image.
- **Parameters**:
    - `result`: Image with the swapped face.
    - `target_image`: Original target image.
    - `mask`: Face mask for blending.
    - 
## Example Usage
- **Source Face**: /path/to/source.jpg
- **Target Face**: /path/to/target.jpg

Run the program and provide the above paths when prompted. The resulting image will display the swapped face.

## Output
- The output image is displayed directly in the notebook or script.
- You can modify the script to save the output locally.

## Error Handling
- Handles invalid user inputs (e.g., incorrect file paths or unsupported image formats).
- Provides descriptive error messages for debugging.

## Author
This project was developed as a face-swapping tool to demonstrate image processing and facial landmark techniques in Python. Feel free to enhance or customize it further!
