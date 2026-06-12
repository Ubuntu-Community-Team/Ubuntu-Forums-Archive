---
title: "DVI not working"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by Mauleye on 2005-05-29
Hi

My problem:

Since I installed the NVIDIA Drivers the DVI interface on my Asus 6600GT doesn't send any signals when X is stated.

Any ideas?

---

### Post by Mauleye on 2005-06-01
RTFM ;)

I found a hint [here](http://www.ubuntuforums.org/showthread.php?t=31448&highlight=DVI)

The solution for me personaly was to set the ConnectedMonior-String-Option in my xorg.config like this:

```
Section "Device"
(...)
Option    "ConnectedMonitor"    "DFP"
(...)
SectionEnd
```  

The problem was that the monitor-detection didn't work for me... why ever... so I had to tell the driver which monitor(s) is/are connected.

Btw: DFP = digital flat panel - other Options are TV and CRT which is default if detection failed.

---

