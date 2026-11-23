# EXP-3-Record-Histogram-processing-Completion-requirements

# Aim
To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

  • Read and display a grayscale image
  • Plot histogram of the grayscale image
  • Apply histogram equalization on grayscale image
  • Read and display a color image
  • Plot histogram of B, G, R channels
  • Convert image to HSV color space
  • Apply histogram equalization on the Value (V) channel
  • Convert the enhanced image back to BGR format
  • Display original and enhanced images with histograms
# Software Used
 • Anaconda – Python 3.7
 • Jupyter Notebook / VS Code
 • OpenCV (cv2)
 • NumPy
 • Matplotlib
# Algorithm
# Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

# Step 2:
Read the image parrot.jpg in grayscale format.

# Step 3:
Display the grayscale image and plot its histogram.

# Step 4:
Apply histogram equalization using cv2.equalizeHist() to enhance contrast.

# Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

Step 6:
Read the same image in color format.

# Step 7:
Split the image into B, G, R channels and plot their histograms.

# Step 8:
Convert the image from BGR to HSV color space.

# Step 9:
Apply histogram equalization on the V (Value) channel.

# Step 10:
Merge the channels and convert the image back to BGR format.

# Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

# Program

Developed By:
Name: Rasiga S


Register No:212225220081
# Grayscale Histogram Equalization
```
import cv2
import matplotlib.pyplot as plt

# Read the grayscale image
img = cv2.imread('i1.jpg', cv2.IMREAD_GRAYSCALE)

# Check whether image is loaded
if img is None:
    print("Image not found!")
else:
    # Perform histogram equalization
    equalized = cv2.equalizeHist(img)

    # Display original and enhanced images
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(img, cmap='gray')
    plt.title('Original Grayscale Image')
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.imshow(equalized, cmap='gray')
    plt.title('Histogram Equalized Image')
    plt.axis('off')

    # Histogram before enhancement
    plt.subplot(2, 2, 3)
    plt.hist(img.ravel(), 256, [0, 256])
    plt.title('Histogram Before Equalization')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    # Histogram after enhancement
    plt.subplot(2, 2, 4)
    plt.hist(equalized.ravel(), 256, [0, 256])
    plt.title('Histogram After Equalization')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    plt.tight_layout()
    plt.show()




```

# Color Image Histogram Equalization
```

import cv2
import matplotlib.pyplot as plt

# Read the original color image
img = cv2.imread('i2.jpg')

# Check whether image is loaded
if img is None:
    print("Image not found!")

else:
    # Convert BGR to RGB for display
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Convert BGR to HSV
    hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

    # Split HSV channels
    h, s, v = cv2.split(hsv)

    # Perform histogram equalization on V channel
    v_equalized = cv2.equalizeHist(v)

    # Merge HSV channels
    hsv_equalized = cv2.merge((h, s, v_equalized))

    # Convert HSV back to BGR
    equalized = cv2.cvtColor(
        hsv_equalized,
        cv2.COLOR_HSV2BGR
    )

    # Convert enhanced image to RGB
    equalized_rgb = cv2.cvtColor(
        equalized,
        cv2.COLOR_BGR2RGB
    )

    # Display original and enhanced images
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(img_rgb)
    plt.title('Original Color Image')
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.imshow(equalized_rgb)
    plt.title('Histogram Equalized Color Image')
    plt.axis('off')

    # Histogram before enhancement (B, G, R)
    plt.subplot(2, 2, 3)

    colors = ('b', 'g', 'r')

    for i, color in enumerate(colors):
        hist = cv2.calcHist(
            [img], [i], None, [256], [0, 256]
        )
        plt.plot(hist, color=color)

    plt.title('Histogram Before Equalization')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    # Histogram after enhancement
    plt.subplot(2, 2, 4)

    for i, color in enumerate(colors):
        hist = cv2.calcHist(
            [equalized], [i], None, [256], [0, 256]
        )
        plt.plot(hist, color=color)

    plt.title('Histogram After Equalization')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')

    plt.tight_layout()
    plt.show()

    # Save enhanced image
    cv2.imwrite('color_equalized.jpg', equalized)

    print("Color Histogram Equalization completed!")
    print("Enhanced image saved successfully!")

```
# Output
# Grayscale Histogram Equalization
Original grayscale image is displayed
Histogram of original grayscale image is plotted
Enhanced image after histogram equalization is displayed
Histogram of enhanced grayscale image shows improved contrast


<img width="782" height="505" alt="image" src="https://github.com/user-attachments/assets/60fd14d2-0070-4cd9-9795-7e991b83e1a4" />


# Color Image Histogram Equalization
Original color image is displayed
Histogram of B, G, R channels is plotted
Enhanced image after HSV-based equalization is displayed
Histogram of enhanced image shows better intensity distribution



<img width="835" height="498" alt="image" src="https://github.com/user-attachments/assets/68aad1e6-8fd2-4642-abba-faaeeb3b65e2" />


# Result
Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
