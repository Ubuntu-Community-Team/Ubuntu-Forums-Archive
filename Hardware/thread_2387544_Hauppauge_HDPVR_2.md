---
title: "Hauppauge HDPVR 2"
date: 2018-03-20
forum: Hardware
---

### Post by don43 on 2018-03-20
I have the PVR 2 working on a Linux machine, but it is only recording in the default 6mbps bitrate . Is there a way to change the bitrate?  Called Hauppauge but was told they do not offer support for Linux

---

### Post by TheFu on 2018-03-20
I don't use this since my 1512 got fried, but there are settings in the common/settings.cfg file:
```
BitRate=2000000
BitRatePeak=2500000
BitRateMode=0
``` for the test code Haupauge provided. The version I have is from 2014, so almost positively out of date.  I have no idea if those settings are even used and cannot test. 

Sorry.

---

