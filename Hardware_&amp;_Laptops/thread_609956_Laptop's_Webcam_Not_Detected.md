---
title: "Laptop's Webcam Not Detected"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by Mongoose.wa on 2007-11-11
My laptop's webcam isn't detected by Ubuntu. According to [this guide](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/) on installing gutsy on my laptop specifically, my webcam should work out of the box. I've tried installing uvcvideo, camorama, and luvcview, but no dice.

When i run luvcview in the terminal, it returns this:
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

When I run camorama, a dialogue box pops up saying "Could not connect to video device (/dev/video0). Please check connection."


How do I get Ubuntu to detect my webcam?

---

### Post by GERGE on 2007-12-12
I have the same problem right now, still working on it?

Any ideas?

---

### Post by c1rcu17 on 2008-01-02
If you are on the IFL90, the I can attest that the web cam does work. I'm on the IFL90 and Gusty now, and the cam does work with Ekiga, but I haven't tried any other programs with it.

---

### Post by henriquemaia on 2008-01-19
> **c1rcu17 said:**
> If you are on the IFL90, the I can attest that the web cam does work. I'm on the IFL90 and Gusty now, and the cam does work with Ekiga, but I haven't tried any other programs with it.

I have an IFL90 and my camera worked out of the box too. But recently I made a reinstallation of gutsy and the camera is not detected. Can&#8217;t figure out why.

Update: oops, wrong kernel. I was using a different kernel without drivers. I have already corrected this by using a driver-enabled kernel.

---

### Post by chubs on 2008-02-09
> Update: oops, wrong kernel. I was using a different kernel without drivers. I have already corrected this by using a driver-enabled kernel.

Could you go into more detail?

---

### Post by cdtech on 2008-02-09
List the results:
```
lsusb
```

---

### Post by chubs on 2008-02-10
Bus 005 Device 002: ID 03f0:4d11 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 147e:2016  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f2:b018 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000

---

