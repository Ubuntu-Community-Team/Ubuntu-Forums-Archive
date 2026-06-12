---
title: "Latitude E6400 Scrolling feature on touchpad does not work under Ubuntu"
date: 2008-09-06
forum: Hardware
---

### Post by Dovis on 2008-09-06
Hi,

When I installed Ubuntu 8.04 the scrolling on the touchpad didnt work. If anybody has any ide how to solve the problems or know where I can get that info it would be great. 

I found a solution for an inspirion/Ubuntu 7 but im not sure it will work with latitude/Ubuntu 8.04. 

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work)

Edit. tpconfig tells me this;
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

Kind regards

Dovis

 

Dell Latitude | E6400

OS: Ubuntu 8.04 (Linux)

*Intel® Core&#8482; 2 Duo P8400(2.26GHz,1066MHz, 3MB)
*2GB 800MHz DDR2 memory (2 x 1GB)
*200GB serial ATA HDD 7200RPM (Free Fall Sensor)
*Intel WiFi Link 5300 (802.11 a/g/n 3X3) 1/2 MiniCard with Centrino label
*Mobile Intel® Graphics Media Accelerator X4500HD With Express Card

---

### Post by ledruide on 2008-09-07
hi,
Try to configure your touchpad with "gsynaptics".

---

### Post by hasinasi on 2008-09-15
I have the same problem here. 
From what I can tell, the touchpad is not recognized by X *at all*. (cat /proc/bus/input/devices does not show anything except a PS/2 mouse). Some of my experiences are posted in this thread: [http://forum.notebookreview.com/showthread.php?t=298130]("http://forum.notebookreview.com/showthread.php?t=298130")

Does this need a kernel fix? BIOS update? 
I tried 8.10-alpha 5 (2.6.27) as well as 8.04 (2.6.24). Same problem in both cases. 

> **ledruide said:**
> hi,
Try to configure your touchpad with "gsynaptics".

I do not think that "gsynaptics" does anything for reasons mentioned above. This should be equivalent to using synclient, which gives error messages, as the touchpad is not recognized by the BIOS. 

Any ideas anybody what to do here? 
--hasi

---

### Post by hasinasi on 2008-09-15
I just filed a bug on this issue: 

[https://bugs.launchpad.net/ubuntu/+bug/129477]("https://bugs.launchpad.net/ubuntu/+bug/129477")

---

### Post by hasinasi on 2008-09-17
Ooops...

I just realized that I posted the wrong link in my previous post. Sorry! The correct bug number is 270643: 

[https://bugs.launchpad.net/ubuntu/+bug/270643]("https://bugs.launchpad.net/ubuntu/+bug/270643")

The bug linked in my previous post is a similar one in an older Dell model. It may be a systematic problem, that every time they add new ALPS touchpads to a DELL system, it is not recognized by the kernel.

--hasi

---

