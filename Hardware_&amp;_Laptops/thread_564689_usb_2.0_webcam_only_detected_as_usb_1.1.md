---
title: "usb 2.0 webcam only detected as usb 1.1"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by ireneshusband on 2007-10-01
I have a logitech quickcam pro that is most definitely a usb 2.0 device, but it only shows up in feisty as a usb 1.1 device, which means that I can only capture video at a low resolution. I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+bug/133266") some while back, but there doesn't seem to be any progress on it so far, so I was wondering if anyone here might be able to point me in the right direction...

Many thanks

---

### Post by peabody on 2007-10-01
Do you know what kernel module is used to drive the camera?  Running a modinfo command on the module name might reveal some parameters that you might be able to play with, although methinks that if the driver could support it, it would be able to autodetect it.

---

### Post by geraldm on 2007-10-01
The bug report should be changed to "need driver for quickcam pro".

The camera is being reported as 1.1 because the camera is using vendor-specific protocol.
Using usb 1.1 to communicate with the device is the default behaviour.  When a driver
is found for the camera, it will claim the device and use high speed.  
This is not a bug with USB.

Search for a driver for the camera.

Gerald

---

### Post by ireneshusband on 2007-10-02
The camera uses the gspca driver. I'll have to wait a day or two to get back onto the box in question to run modinfo.

---

### Post by ireneshusband on 2007-10-02
I have uploaded the output of "modinfo gspca" to the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/133266").

---

