#Make a white outline around the image we have inputed /it cud be any colour according to the value we input to it.

#image-manipulation
#set of programs to manipulate images 
import cv2  
import numpy as np 
import matplotlib.pyplot as plt
from google.colab.patches import cv2_imshow

!curl -o image.jpeg https://www.slashgear.com/wp-content/uploads/2014/11/eiffel-tower-at-night-hd-wallpapers-820x420.jpg
img = cv2.imread('image.jpeg', 1)

img=cv2.resize(img,(500,500)) #this is to resize the images into a prescibed size 500, 500
imgc=np.copy(img)
imgc[:,:,:]=0
edges = cv2.Canny(img,100,200)

imgc[:,:,0]=edges
imgc[:,:,1]=edges
imgc[:,:,2]=edges

img[imgc==255]=255 # <--this is the main hero of the code

cv2_imshow(img)
