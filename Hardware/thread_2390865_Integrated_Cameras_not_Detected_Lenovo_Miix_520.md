---
title: "Integrated Cameras not Detected Lenovo Miix 520"
date: 2018-05-03
forum: Hardware
---

### Post by mickpick on 2018-05-03
Very new to Ubuntu... 

Lenovo Miix 520 (Very new hardware) 

The integrated cameras are not detected.   I've scoured forums for ways to get working but am running up empty handed. 

-Version-
Kernel		: Linux 4.13.0-39-generic (x86_64)
Version		: #44-Ubuntu SMP Thu Apr 5 14:25:01 UTC 2018
C Library		: GNU C Library / (Ubuntu GLIBC 2.26-0ubuntu2.1) 2.26
Distribution		: Ubuntu 17.10


-Input Devices-
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
[B] Video Bus
                     [/B]
 Intel Virtual Button driver
 HDA Intel PCH Mic
 HDA Intel PCH Headphone
 HDA Intel PCH HDMI/DP,pcm:3
 HDA Intel PCH HDMI/DP,pcm:7
 HDA Intel PCH HDMI/DP,pcm:8
 HDA Intel PCH HDMI/DP,pcm:9
 HDA Intel PCH HDMI/DP,pcm:10
 Keyboard K780
 Logitech M705
 Logitech MK700
 Jabra SPEAK 410 USB



What info can i provide?

---

### Post by slickymaster on 2018-05-03
*Thread moved to **Hardware**.*

---

### Post by mörgæs on 2018-05-05
When using new hardware one should use the newest of software. 

How does 18.04 work?

---

### Post by mickpick on 2018-05-06
Thanks. 

I upgraded to 18.04  Still not detected.

---

### Post by ismaelteodoro on 2018-05-07
on ubuntu 18.04
check udev rules
check by ~#udevadm monitor (plug and unplug device several times)
check permissions on ~#ls -la /dev/bus/usb/xxx/xxx/
~#crw------- 1 root root 189, 19 mai  7 21:55 020

---

### Post by tunghim on 2018-11-16
Same issue. Ubuntu 18.10, Lenovo Miix 520.

---

