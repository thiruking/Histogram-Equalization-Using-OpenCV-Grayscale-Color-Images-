# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program
```py
# Import required libraries

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image in grayscale format

gray=cv2.imread("parrot.jpg",0)
plt.imshow(gray)
plt.axis("off")

# Display the grayscale image.
plt.imshow(gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

# Plot the histogram of the grayscale image

plt.hist(gray.ravel(), 256, [0,256])
plt.title("Histogram of Grayscale Image")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()

# Perform histogram equalization

equalized = cv2.equalizeHist(gray)

# Display [1] the Original Image (Gray Image) and its Histogram, and [2] the Enhanced Image and its Histogram using a 2×2 layout in Matplotlib.

plt.figure(figsize=(12,10))
plt.subplot(2,2,1)
plt.imshow(gray, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.hist(gray.ravel(), 256, [0,256])
plt.title("Histogram of Original Image")

plt.subplot(2,2,3)
plt.imshow(equalized, cmap='gray')
plt.title("Enhanced Image")
plt.axis("off")

plt.subplot(2,2,4)
plt.hist(equalized.ravel(), 256, [0,256])
plt.title("Histogram of Enhanced Image")

plt.tight_layout()
plt.show()



# Plot the histogram of colour image

colors = ('b', 'g', 'r')

for i, col in enumerate(colors):
    hist = cv2.calcHist([img], [i], None, [256], [0,256])
    plt.plot(hist, color=col)

plt.title("Histogram of Color Image")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()


# Convert to HSV.

hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

# Perform histogram equalization

H, S, V = cv2.split(hsv)
V_eq = cv2.equalizeHist(V)
hsv_eq = cv2.merge((H, S, V_eq))

# Convert back to BGR format

enhanced_bgr = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)


# Display

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
enhanced_rgb = cv2.cvtColor(enhanced_bgr, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(12,10))

plt.subplot(2,2,1)
plt.imshow(img_rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(2,2,2)

colors = ('b', 'g', 'r')

for i, col in enumerate(colors):
    hist = cv2.calcHist([img], [i], None, [256], [0,256])
    plt.plot(hist, color=col)

plt.title("Histogram of Original Image")

plt.subplot(2,2,3)
plt.imshow(enhanced_rgb)
plt.title("Enhanced Color Image")
plt.axis("off")

plt.subplot(2,2,4)

for i, col in enumerate(colors):
    hist = cv2.calcHist([enhanced_bgr], [i], None, [256], [0,256])
    plt.plot(hist, color=col)

plt.title("Histogram of Enhanced Image")

plt.tight_layout()
plt.show()



```

### Developed By:
## Name: THIRUMAKAI K

### Register No: 212224240176 

---

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed
  <img width="642" height="471" alt="image" src="https://github.com/user-attachments/assets/95b3c40e-33b4-4cca-b438-0239a59eae83" />


- Histogram of original grayscale image is plotted
<img width="746" height="571" alt="image" src="https://github.com/user-attachments/assets/a0e75db2-d8a7-46d6-a4d7-78702409d1d5" />

  
- Enhanced image after histogram equalization is displayed

- <img width="1366" height="573" alt="image" src="https://github.com/user-attachments/assets/d1bc0eab-8853-4d88-80f3-2d0132878483" />
  

### Color Image Histogram Equalization

- Original color image is displayed
  <img width="778" height="570" alt="image" src="https://github.com/user-attachments/assets/14cf5694-8efb-4133-abc0-6f0d39cd2ef6" />

- Histogram of B, G, R channels is plotted
- <img width="863" height="680" alt="image" src="https://github.com/user-attachments/assets/589fe44a-9918-44f0-8dc4-98da0e5a057d" />

- Enhanced image after HSV-based equalization is displayed
- <img width="857" height="671" alt="image" src="https://github.com/user-attachments/assets/ed0aac69-6669-46db-bd44-23167bf112b2" />

- Histogram of enhanced image shows better intensity distribution

- <img width="757" height="607" alt="image" src="https://github.com/user-attachments/assets/3d5def35-8902-4736-b3eb-516c80db4b9f" />


---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
