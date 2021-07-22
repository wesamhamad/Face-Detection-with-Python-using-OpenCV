# Face Detection with Python using OpenCV
Face detection is a computer vision technology that helps to locate/visualize human faces in digital images, videoes and real time detection using cameraes. With the advent of technology, face detection has gained a lot of importance in many recognition systems, for different purpose .

![dd](https://user-images.githubusercontent.com/74800962/126720183-22c32e35-ff9b-4b74-96c6-ea5ca2143309.png)

## Installation 

You need to i nstall opencv library.

Run this command to  install it (opencv for python3):
```
pip3 install opencv-contrib-python
```
Then import the package in your code (file.py):
```
import cv2
```
## Recognize Face using OpenCV
#### Download the dependencies files:
1. [haarcascade_eye.xml] 
2. [haarcascade_frontalface_default.xml]
#### Then run the following code and it will perform face detection on the given image.

```python
import cv2

face_cascade = cv2.CascadeClassifier(
    '/Users/wesam/Documents/f/Real-time-detection-using-OpenCV-main 2/haarcascade_frontalface_default.xml')


eye_cascade = cv2.CascadeClassifier(
    '/Users/wesam/Documents/f/Real-time-detection-using-OpenCV-main 2/haarcascade_eye.xml')

cap = cv2.VideoCapture(0)

while 1:
    ret, img = cap.read()
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = face_cascade.detectMultiScale(gray, 1.3, 5)

    for (x, y, w, h) in faces:
        cv2.rectangle(img, (x, y), (x + w, y + h), (255, 0, 0), 2)
        roi_gray = gray[y:y + h, x:x + w]
        roi_color = img[y:y + h, x:x + w]

        eyes = eye_cascade.detectMultiScale(roi_gray)
        for (ex, ey, ew, eh) in eyes:
            cv2.rectangle(roi_color, (ex, ey),
                          (ex + ew, ey + eh), (0, 255, 0), 2)

    cv2.imshow('img', img)
    k = cv2.waitKey(30) & 0xff
    if k == 27:
        break

cap.release()
cv2.destroyAllWindows()
```
`` 
NOTE:You have to change the path of files base on yours, 
cv2.CascadeClassifier(your file path)
``

#### After running the [code](), it will draw rectangles around the faces and eyes as shown in the output sample below.

https://user-images.githubusercontent.com/74800962/126720441-470e7298-4b41-454d-a4bb-1284be40cfa9.mov

