---
title: "Weird results on bumblebee/nvidia proprietary benchmarks"
date: 2014-03-23
forum: Hardware
---

### Post by Zorgoth on 2014-03-23
I'm using Ubuntu 14.04 and aGT 635M Optimus system. For some reason, glxgears and glmark2 are about 3 times faster without optirun than they are with it. glmark2 claims that I am using Intel by default and NVIDIA when I use optirun, although I don't know how it checks. For glxgears I get ~6000fps without optirun and so.mewhere above 2000 with optirun (this is after setting vblank_mode=0).

Is this really Intel graphics outperforming NVIDIA due to bumblebee being inefficient, or is my default graphics driver NVIDIA?

I usually would rather be using Intel so as to conserve battery life.

---

