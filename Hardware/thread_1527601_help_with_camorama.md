---
title: "help with camorama"
date: 2010-07-09
forum: Hardware
---

### Post by bjlockie on 2010-07-09
The error that is displayed says I don't have /dev/video0 but I do.
Further debugging found the real error.
Does any know how to fix it?

$ lsusb
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera


$ camorama -D

VIDIOCGCAP
device name = USB 2.0 Camera
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 640
max height = 480
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 320
height = 240
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 320
height = 240
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 33279
hue = 33587
colour = 32768
contrast = 32768
whiteness = 4287
colour depth = 16
YUYV
VIDIOCGMBF  --  could not set buffer info, exiting...

---

