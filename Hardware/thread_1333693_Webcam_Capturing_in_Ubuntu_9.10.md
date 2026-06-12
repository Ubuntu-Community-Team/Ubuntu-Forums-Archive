---
title: "Webcam Capturing in Ubuntu 9.10"
date: 2009-11-21
forum: Hardware
---

### Post by jiapei100 on 2009-11-21
I think this is absolutely an annoying issue which harassed me for quite a long time.

As can be seen from the attached two screen shots
1) The first one is the result when I run "cheese" -- you may grab it directly from Ubuntu repository.
2) The second picture is the result when I run "jmstudio" -- yes, JMF.

I am now using Ubuntu 9.10 + USB webcam Logitech Pro 4000.
Well, yes, I plugged my Logitech QuickCam Pro 4000 (046d:08b2) into the computer after the computer had been booted.



```
There are two situations that I always confront the "failure of webcam capturing".
a) the system failed to detect the webcam because OS booted first and webcam plugged in second.
b) the system detected the webcam and captured image correctly. Afterwards, I plugged the webcam out of the computer.
And then, plug it back into the computer. The webcam didn't work any longer.
```

So, is there a standard solution to refresh webcam capturing?
I mean, whenever I meet such situations, is there a standard solution to make the webcam working again without rebooting?


By the way, the following is my output for "lsusb" and "ls -l /dev/video0".

```
jiapei@jiapei-laptop:/dev$ lsusb
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04fc:0c25 Sunplus Technology Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jiapei@jiapei-laptop:/dev$ ls -l /dev/video0
crw-rw----+ 1 root video 81, 0 2009-11-18 20:10 /dev/video0
```



Any suggestions?
Thanks very much.

JIA Pei

---

