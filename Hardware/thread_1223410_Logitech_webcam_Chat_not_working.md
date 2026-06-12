---
title: "Logitech webcam Chat not working"
date: 2009-07-26
forum: Hardware
---

### Post by graphicsxp on 2009-07-26
Hi,

I have Ubuntu Jaunty and I'm trying to get my webcam to work; but no luck so far.... I've tried with many applications including Kopete and Cheese but although the webcam is listed, the picture remains black or non-sense colours.

lsusb gives :

Bus 001 Device 010: ID 046d:092c Logitech, Inc. QuickCam Chat

lsmod | grep gspca gives :

gspca_spca561          18944  1 
gspca_main             29952  3 gspca_spca561
videodev               41600  2 uvcvideo,gspca_main


Any idea what I can do  ?

Thanks

---

