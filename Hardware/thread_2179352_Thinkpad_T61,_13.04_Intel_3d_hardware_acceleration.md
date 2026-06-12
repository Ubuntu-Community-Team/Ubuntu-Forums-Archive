---
title: "Thinkpad T61, 13.04 Intel 3d hardware acceleration"
date: 2013-10-07
forum: Hardware
---

### Post by scott25 on 2013-10-07
I have a Thinkpad T61, It has the Intel x3100 in it. I installed the Open intel drivers and Mesa utilities. Unity is running, not slow but has hickups and compiz is slow or doesn't work sometimes and crashes. I have seen people getting almost 1000 FPS in glxgears(mesa-utils to test acceleration) and I am gettign only around 60. Besides installing the open intel drivers what should I do to have hardware acceleration. I have been searching for this everywhere.

Thanks

---

### Post by Yellow Pasque on 2013-10-08
> I have seen people getting almost 1000 FPS in glxgears(mesa-utils to test acceleration) and I am gettign only around 60.
glxgears is not a benchmark. Video sync is turned on by default (to prevent ugly video tearing), so 60Hz monitor = 60fps

---

