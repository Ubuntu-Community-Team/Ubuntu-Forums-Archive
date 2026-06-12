---
title: "Only low webcam resolution (176x144) supported =("
date: 2009-01-20
forum: Hardware
---

### Post by wolterh on 2009-01-20
Hi, I've been using my m1530 for some weeks now, and for a similar lapse, I've been trying to know why I can't use my webcam in cheese with a larger resolution than 176x144.

My webcam is detected by lsusb as Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.

uvcvideo is loaded

gspca returns "FATAL: Module gspca not found." when I try to modprobe it. I found many files and folders under the name of gspca in a filesystem search I did, which tells me that I do have the module, maybe, and the problem can be that it is not in the right place, for it is not found at load time.

Any more information that you need, I will answer briefly. Thanks in advance.

---

### Post by wolterh on 2009-03-28
[http://ubuntuforums.org/showthread.php?t=1035280](http://ubuntuforums.org/showthread.php?t=1035280)

---

