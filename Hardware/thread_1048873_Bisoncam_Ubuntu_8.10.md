---
title: "Bisoncam Ubuntu 8.10"
date: 2009-01-23
forum: Hardware
---

### Post by rmccarri on 2009-01-23
Hi everyone,
I'm trying to get all of the hardware woorking on my Lenovo V100 laptop.  I have a Bisoncam webcam and followed the following instructions

[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#5986:0203_BisonCam_.28Acer.29](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#5986:0203_BisonCam_.28Acer.29)

and the camera is giving a picture in both Xsane and Cheese, but it is only showing the upper right portion of the CCD image.  It's a 1280X960 camera, but it will only display at 640X480 in the upper left quadrant.  Has anyone else found a fix for this?

Also, I would like to use the camera with Skype, but I only get a green static mess.

Any help would be greatly appreciated!

---

### Post by rmccarri on 2009-01-24
Just a little more information, it appears to be an Ali Corp. M5602 camera.

---

### Post by rmccarri on 2009-01-25
Here is some more information, in case it helps,  lsusb gives the following for the device:

Bus 005 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller

In looking around, it seems like there are some sites that were targeted at making a set of drivers for this camera, but they seem to have died a while back.  Has anyone out there gotten this camera to work?

---

### Post by rmccarri on 2009-01-25
I found this post with directions on installing the drivers:

[http://ubuntuforums.org/showpost.php?p=5055135&postcount=6](http://ubuntuforums.org/showpost.php?p=5055135&postcount=6)

Everything goes well until the last step, where "sudo modprobe m5602" gives the following message:

FATAL: Error inserting m5602 (/lib/modules/2.6.27-9-generic/kernel/drivers/usb/media/m5602.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by rmccarri on 2009-02-26
Hi all,
I was able to get the drivers installed sans errors.  The camera light turns on, but the camera is still not functioning.  Has anyone gotten the m5602 camera drivers working on the V100?

---

### Post by rmccarri on 2009-03-01
More information:

Running programs that try to access the camera gives the following error:

libv4l2: error dequeuing buf: Input/output error
[00000409] v4l2 demux error: Failed to wait (VIDIOC_DQBUF)

---

### Post by Tankerdog2002 on 2009-03-11
I'm having the same problems. Just bought a new MALIBAL satori. Apparently these new 'Chineeeeeese machines have all kinds of hardware that's incompatible with Ubuntu.
 
No webcam....no fingerprint reader...

Any suggestions? Anyone? 


'Argggggggggggggh!!!   I don't want to go back to Winbloze.

---

