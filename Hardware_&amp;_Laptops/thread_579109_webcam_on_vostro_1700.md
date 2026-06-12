---
title: "webcam on vostro 1700"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by jsgarvin on 2007-10-18
I've been running Feisty on my Vostro 1700 for a while now and just started tinkering with trying to get the integrated webcam working.  I see some threads with people discussing it, and some seem to have it working, but nobody gives any clear directions on what to do.

I've got Camorama installed, and it complains that there's no device at /dev/video0 (and it's correct, that device doesn't exist).  EasyCam says that same thing.

I installed the Linux-uvc drivers as mentioned in one thread.  that didn't seem to do squat.

So, anybody got any suggestions?  Thanks!

---

### Post by jsgarvin on 2007-10-18
bump

---

### Post by toorima on 2007-10-18
for me it just worked using the v4l2 driver installed by default , works in cheese, amsn and ekiga
on a vostro 1500 and using gutsy RC

---

### Post by jsgarvin on 2007-10-21
Installed Gutsy today and... it just worked.  WhoHoo!

---

### Post by DerPflanz on 2007-10-28
Could you tell me what drivers and settings you are using? I have Gutsy installed and am using the uvcvideo driver to talk to the webcam (Dell Vostro 1700). v4l-info gives a lot of info about the cam, but I cannot grab anything; camorama tells me it cannot connect to /dev/video0 and all other programs just crash.

Mplayer gets me some extra info, after seemingly correct initialisation:
v4l2: ioctl dequeue buffer failed: Invalid argument, idx = 0


Some extra info:

$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 

$ v4l-info
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "Laptop Integrated Webcam"
        bus_info                : "0000:00:1d.7"
        version                 : 0.1.0
        capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]
<snip>

---

### Post by sfil on 2007-11-05
hi,
i ve a vostro 1500 and the same problems. i run the ubuntu 7.10. I think that it is the same webcam as the vostro 1700.

the webcam works width Ekiga and kdetv: 
sudo apt-get install kdetv

---

### Post by lokutus25 on 2007-11-11
I found the help from this web site very helpful: [www.rastageek.org](www.rastageek.org).
You can find it also in [https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x).

---

