---
title: "Programs can't access webcam (/dev/video0), flash can however"
date: 2010-02-17
forum: Hardware
---

### Post by Tresmius on 2010-02-17
.

---

### Post by gordintoronto on 2010-02-17
What version of Ubuntu are you using?  Jaunty had a patch for Advent UVC webcams. It's described here:
[http://launchpadlibrarian.net/19897435/0006-V4L-DVB-9030-uvcvideo-Add-support-for-Advent-42.patch](http://launchpadlibrarian.net/19897435/0006-V4L-DVB-9030-uvcvideo-Add-support-for-Advent-42.patch)

---

### Post by no2498 on 2010-02-17
open a terminal type ( gstreamer-properties ) click enter
now if you change anything flash may not work again


click video try v4l1 or v4l2
click the bottom test button
for each 1

try the cam in your programs

---

### Post by Tresmius on 2010-02-17
.

---

### Post by Tresmius on 2010-02-18
.

---

### Post by afrodeity on 2010-03-28
libv4l2: error getting capabilities: Inappropriate ioctl for device

---

