---
title: "Fix input/output error or find correct webcam driver for icecam2?"
date: 2010-03-26
forum: Hardware
---

### Post by datababy on 2010-03-26
I have an icecam2 webcam (ID 0ac8:3420) (Sirius USB 2.0 camera). I run Ubuntu 9.10.

When I plug it in, /var/log/messages shows that uvcvideo has been loaded and has found a uvc 1.00 device. 

When I run luvcview, I get the following error message:

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
  Frame size:   352x288 (requested size 640x480 is not supported by device)
  Frame rate:   5/1 fps (requested frame rate 30 fps is not supported by device)
Unable to start capture: Input/output error
Error grabbing
Cleanup done. Exiting ...

I have two questions. 

1) Apparently, the webcam is being detected. Some communication must be taking place since the computer knows the device's resolution. How do I fix the input/output error? I've tried setting the permissions for /dev/video0 to 777.

2) Most of what I've found via google suggests the gspca driver for this webcam. lsmod | grep gspca shows nothing, so I do not have it loaded. My question is: which gspca driver would I load? 

ls of the appropriate kernel driver directory shows:
gspca_conex.ko       gspca_pac207.ko   gspca_spca506.ko  gspca_tv8532.ko
gspca_etoms.ko       gspca_pac7311.ko  gspca_spca508.ko  gspca_vc032x.ko
gspca_finepix.ko   gspca_sn9c20x.ko  gspca_spca561.ko  gspca_zc3xx.ko
gspca_main.ko       gspca_sonixb.ko   gspca_sq905c.ko   m5602
gspca_mars.ko       gspca_sonixj.ko   gspca_sq905.ko    stv06xx
gspca_mr97310a.ko  gspca_spca500.ko  gspca_stk014.ko
gspca_ov519.ko       gspca_spca501.ko  gspca_sunplus.ko
gspca_ov534.ko       gspca_spca505.ko  gspca_t613.ko

As far as I can tell, there is no &quot;main&quot; driver. How do I determine which one applies to my webcam?

Thanks in advance

(BTW, I've already seen the ubuntu webcam page. It hasn't helped.)

---

### Post by datababy on 2010-03-26
Fixed! The problem was USB bandwidth. Can't use the camera through a USB hub.

---

