---
title: "Acer 5920 webcam works at low resolution only"
date: 2008-12-25
forum: Hardware
---

### Post by beyboo on 2008-12-25
I filed the following bug report at launchpad for a funny issue with my Acer 5920 webcam. Cheese does not work with the 640x480 resolution. It works at the lowest available resolution. Its funny cause, it worked pefect on Hardy earlier and also worked OK when I first boot intrepid from a live CD and installed Cheese to test if all my hardware was supported in intrepid.

Any help is appreciated. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311320](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311320)

Have an Acer 5920 series ZD1 model laptop with acer orbicam found as below :
[ 14.595372] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[ 14.597417] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-2/3-2:1.0/input/input7
[ 14.597507] usbcore: registered new interface driver uvcvideo
[ 14.597511] USB Video Class driver (v0.1.0)

The Default input plugin for video in gstreamer-propersties is v4l2, device /dev/video0

The problem
When clicking on test in gstreamer-properties, the test window comes up, however is much lower than default VGA resolution of 640x480

Cheese / skype operate at the resolution of 160x120 only. With any higher configuration I get the following error in cheese.
libv4l2: error allocating conversion buffer

---

### Post by beyboo on 2009-01-24
Jan 2009 intrepid updates resolved issue

[https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009594.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009594.html)
[https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009584.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009584.html)

---

