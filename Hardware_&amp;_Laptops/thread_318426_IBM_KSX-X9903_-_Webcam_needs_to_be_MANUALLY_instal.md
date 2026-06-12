---
title: "IBM KSX-X9903 - Webcam needs to be MANUALLY installed."
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by shogo2040 on 2006-12-14
KSX-X9903 - Webcam is not installed by default in 6.10 (Xubuntu).  After googling for a week, I found out that you need to install it MANUALLY with this command:

$ /sbin/modprobe ibmcam

To verify it is installed, use this command:

$ dmesg | grep "cam"

And you will get the following:

[17181658.728000] drivers/media/video/usbvideo/ibmcam.c: IBM PC Camera USB camera found (model 2, rev. 0x030a)
[17181658.736000] videodev: "ibmcam USB Camera" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[17181658.736000] drivers/media/video/usbvideo/usbvideo.c: ibmcam on /dev/video0: canvas=352x240 videosize=352x240
[17181658.740000] usbcore: registered new driver ibmcam

Now start up up Ekiga and your IBM KSX-X9903 will finally work.

Is there a GUI/Synaptic way of doing this?  I have no idea.  If there is, please reply with instructions on the GUI installation procedure.  Thanks.

SHOGO

---

