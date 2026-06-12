---
title: "NVIDIA G64 GPU Driver Choice"
date: 2016-03-19
forum: Hardware
---

### Post by BlueAZ on 2016-03-19
Hi,   I'm running 14.04 lts on a 64-bit AMD desktop.  The NVIDIA G64 GPU has been running in this machine for a year or more.  Throughout that time, I was using the built-in X-Org graphics driver and all was well.  But there must have been some update to it, as things changed.  I use Psensor to monitor my CPU and GPU heat levels.  CPU is always around 30 C.  GPU was running between 60 to 75 C.  But recently, it started spiking up above 90 C.  I went into Additional Drivers and switched to the top one listed, NVIDIA driver v. 340.96 (proprietary, tested).  Psensor immediately showed the temp dropped to the low 70's C.  I didn't even have to restart.

I'm posting this in case anyone else has this problem, or if I've mis-interpretted the above, or if there's a bug in a recent X-Org update.

---

### Post by mörgæs on 2016-03-20
Thanks, if you mark the thread 'solved' there is a better chance that people will see the advice.

---

