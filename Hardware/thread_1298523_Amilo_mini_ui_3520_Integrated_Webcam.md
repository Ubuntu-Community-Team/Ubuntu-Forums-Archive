---
title: "Amilo mini ui 3520 Integrated Webcam"
date: 2009-10-22
forum: Hardware
---

### Post by eec on 2009-10-22
Hey,

I have a Amilo mini ui 3520 netbook and installed UNR on it. However, I cannot see my integrated webcam. I installed uvc drivers.

In other threads people were finding their webcam models by typing lsusb but it doesnt work, meaning that it doesnt show the webcam.

eec

---

### Post by eec on 2009-10-24
Any help?

---

### Post by no2498 on 2009-10-27
you may need to set the cam to usb
? do you have any program's to see it on
like cheese or wxcam
then try the 
gstreamer-properties
in the terminal
click the video try diff settings

---

### Post by eec on 2009-10-29
i tried all of them but it wasnt detected. however after fresh installation in gstreamer-properties i was able to find it as v4l2

but i still cant see the webcam neither in lsusb nor lspci

---

