---
title: "Acer OrbiCam stopped working on Hardy"
date: 2008-05-31
forum: Hardware
---

### Post by Dj_Deutschi on 2008-05-31
Hello,

I have a strange problem. So my webcam (Acer OrbiCam on Acer Aspire 5610Z) stopped working a month ago. I have no idea how. So I reinstalled uvcvideo many time and the problem is still there. After installing ucview the led is on but there is no output from my webcam. But there camera is working only with luvcview.
Here is the output from luvciew:
```
vladi@vladi-laptop:~$ luvcview 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
find DRI 
find DRI 
find DRI 
find DRI 
find DRI 
find DRI 
find DRI 
...
```
changing some options also work (brightness, light, contrast)

Starting wxcam gives the following output:
```
vladi@vladi-laptop:~$ wxcam
Using video4linux 2 API
Determining pixel format...
pixel format: MJPEG
Found V4L2_PIX_FMT_MJPEG pixel format
pixel format: YUV 4:2:2 (YUYV)
Found V4L2_PIX_FMT_YUYV pixel format
Killed

```
Killed because it just freeze without any notification and without any image from the webcam. But the led is still on. I tried cheese and skype too, but the problem is the same - led is on, but no image. And I sure that  a month ago my webcam was working without any problems out of the box after installing Ubuntu 8.04. 

Any Ideas how to get it working at least in skype?

here is the output from
lsmod | grep uvc:
```
uvcvideo               58376  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
```
and from lsusb:
```
Bus 005 Device 002: ID 5986:0100 Bison Acer OrbiCam
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

P.S. Please excuse my bad english

---

### Post by stedanarh on 2008-06-09
Hi, I have a Acer Aspire 5610Z. I just install Ubuntu Hardy 8.04. My webcam is working under Cheese. In Kopete is not working (yahoo). I invite someone to view my webcam, but the led is off. I go to the settings and I see the image from the webcam there. Anybody know why?

---

### Post by Dj_Deutschi on 2008-06-09
Well my webcam is working now on Hardy. I have just updated the headers and the linux-uvc driver, and everything is working fine.

---

### Post by FredWiersma on 2008-08-21
> **stedanarh said:**
> Hi, I have a Acer Aspire 5610Z. I just install Ubuntu Hardy 8.04. My webcam is working under Cheese. In Kopete is not working (yahoo). I invite someone to view my webcam, but the led is off. I go to the settings and I see the image from the webcam there. Anybody know why?

I have exactly the same with an Acer Aspire 9300 and 8.04. In Kopete I can chat with MSN, but when I press 'send webcam' and 'receive webcam' the other party accepts those invitations but nothing else happens. When the other party initiates the webcam nothing happens at my side. In the Kopete settings the webcam works fine.

Anyone have got this working?

TIA!

---

