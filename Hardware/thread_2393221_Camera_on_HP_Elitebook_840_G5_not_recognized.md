---
title: "Camera on HP Elitebook 840 G5 not recognized"
date: 2018-05-31
forum: Hardware
---

### Post by sandorrobertk94 on 2018-05-31
Hi all,

So i recently got a new laptop for work, namely the HP Elitebook 840 G5, and installed Ubuntu 18.04.
Everything works as expected (or doesn't work as expected, e.g. the fingerprint reader), except for the webcam.

The camera is a Chicony Electronics produced Windows Hello compatible webcam. Now i don't need any of the Windows Hello features, i just need the webcam to work for calls.
I've also tried updating the kernel to the latest stable version, 4.16.13 at the moment, but had no luck with that either.

Here's the output of lsusb :

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b5e7 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 138a:00ab Validity Sensors, Inc. 
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 03f0:a31d Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And everything i found in dmesg regarding uvcvideo :

```
[    5.161922] uvcvideo: Found UVC 1.50 device HP HD Camera (04f2:b5e7)
[    5.163025] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    5.163875] uvcvideo: Failed to query (129) UVC probe control : -75 (exp. 34).
[    5.163881] uvcvideo: Failed to initialize the device (-5).
[    5.164809] uvcvideo: Unknown video format 00000032-0002-0010-8000-00aa00389b71
[    5.164815] uvcvideo: Found UVC 1.50 device HP HD Camera (04f2:b5e7)
[    5.165255] iwlwifi 0000:01:00.0: loaded firmware version 36.e91976c0.0 op_mode iwlmvm
[    5.167348] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    5.168143] uvcvideo: Failed to query (129) UVC probe control : -75 (exp. 34).
[    5.168148] uvcvideo: Failed to initialize the device (-5).
[    5.168182] usbcore: registered new interface driver uvcvideo
```
Any idea on how i could get this camera working for calls ?

---

### Post by sandorrobertk94 on 2018-07-04
After a couple of weeks without using the camera, and trying newer Linux kernel versions, finally today, with version 4.17.4 of the Linux kernel, the camera on the HP Elitebook 840 G5 is working properly.

---

