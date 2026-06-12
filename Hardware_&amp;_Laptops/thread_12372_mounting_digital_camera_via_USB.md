---
title: "mounting digital camera via USB"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by Stefan Koopmanschap on 2005-01-24
Hey all,

I have a bit of a problem with mounting a digital camera via USB. I editted the fstab to point /media/camera to /dev/sda1 so that I can mount my digital camera. This works fine the first time after booting the PC. However, when I unmount, take off the camera to elsewhere to make pictures, come back, connect the camera again, and try to mount again, it gives errors about not knowing the /dev/sda1 device.

Is there any easy way for putting the camera into the fstab? I guess the camera may get a random device or whatever?

Any help is appreciated.

Stefan

---

### Post by ALai on 2005-01-25
I have problem reading pictures from my digital camera too. I can see it under device manager, but I don't know how to load the pictures. Any suggestions?  :neutral:

A Lai

---

### Post by Stefan Koopmanschap on 2005-01-26
[QUOTE=ALai]I have problem reading pictures from my digital camera too. I can see it under device manager, but I don't know how to load the pictures. Any suggestions?  :neutral:

A Lai[/QUOTE]

well, loading the pictures the first time round is not a problem

what you need to do is mount the camera (with most cameras as VFAT). then you can simply access it as another filesystem. You need to ensure though that the camera supports Mass Storage protocol and is actually set to use it. Works fine for both my camera and my wife's

---

