# writing the code to identify single colour in the picture
import cv2
import numpy as np
import matplotlib.pyplot as mpl
img = cv2.imread('C:\Users\Admin\Desktop\IMAGE 1.jpg')
mpl.figure(figsize=(25,10))
mpl.imshow(img)
# the image was uploaded in the format BGR by default by opencv lets convert into RGB
img_RGB=cv2.cvtColor(img,cv2.COL0R_BGR2RGB)
mpl.figure(figsize=(25,10))
mpl.imshow(img_RGB)
# CONVERTING THE GIVEN IMAGE FROM RGB TO HSV
img_HSV=cv2.cvtColor(img_RGB, cv2.COLOR_RGB2HSV)
lower = np.array([36,0,0])                                                            # (hue,saturation,value)
upper = np.array([86,255,255])
mask = cv2.inRange(img_HSV,lower,upper)
mpl.figure(figsize=(25,10))
mpl.imshow(mask)
# REMOVING THE MASK IN ORDER TO SEE EXACTLY THE WANTED COLOR
rem= cv2.bitwise_and(img_RGB,img_RGB,mask=mask)
mpl.figure(figsize=(25,10))
mpl.imshow(rem)




# writing the code to identify multiple colour in the picture
import cv2
import numpy as np
import matplotlib.pyplot as mpl
img = cv2.imread('C:\Users\Admin\Desktop\IMAGE 1.jpg')
mpl.figure(figsize=(25,10))
mpl.imshow(img)
# the image was uploaded in the format BGR by default by opencv lets convert into RGB
img_RGB=cv2.cvtColor(img,cv2.COL0R_BGR2RGB)
mpl.figure(figsize=(25,10))
mpl.imshow(img_RGB)
# CONVERTING THE GIVEN IMAGE FROM RGB TO HSV
img_HSV=cv2.cvtColor(img_RGB, cv2.COLOR_RGB2HSV)
lower1 = np.array([36,0,0])                                                            # (hue,saturation,value)
upper1 = np.array([86,255,255])          #green
lower2 = np.array([100,150,0])
upper2 = np.array([140,255,255])         #blue
mask1 = cv2.inRange(img_HSV,lower1,upper1)
mask2 = cv2.inRange(img_HSV,lower2,upper2)
mask = mask1 + mask2
mpl.figure(figsize=(25,10))
mpl.imshow(mask)
# REMOVING THE MASK IN ORDER TO SEE EXACTLY THE WANTED COLOR
rem= cv2.bitwise_and(img_RGB,img_RGB,mask=mask)
mpl.figure(figsize=(25,10))
mpl.imshow(rem)



# could only learn to detect the colors but not label them as land or water
