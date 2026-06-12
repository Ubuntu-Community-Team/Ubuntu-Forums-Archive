---
title: "Radeon RX 580 stuck at idle clockspeed (300MHz)"
date: 2020-10-12
forum: Hardware
---

### Post by saphirakai on 2020-10-12
This is likely not an issue with Ubuntu itself, but these forums are the best resource I know of to ask for help...

My GPU (AMD Radeon RX 580 8GB) has been stuck at 300MHz for the last few days and despite being all over the internet looking for a fix, I haven't found anything that works. I used to fix this problem by using CoreCtrl to override the default GPU settings and allow it to hit its maximum stable speed of 1436MHz, however for some reason this has stopped working. CoreCtrl is at the latest version, and my GPU behaves normally on Windows. The one vague fix I've seen suggested setting the pp_od_mclk and pp_od_sclk values to above 0, but that didn't do anything. GPU is still locked at 300MHz and this makes it impossible to reliably use Blender or play any games. Not to mention putting a pretty big damper on my attempting to learn OpenCL...

Has anybody encountered this issue, and even if you haven't, can you think of anything I should try?

---

### Post by Yellow Pasque on 2020-10-13
If you try a LiveUSB of Ubuntu 20.10, do you have the same problem? (20.10 is still technically a beta, but if you're not installing it, don't worry about that.)

---

