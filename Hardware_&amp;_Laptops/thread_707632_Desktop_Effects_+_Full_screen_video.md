---
title: "Desktop Effects + Full screen video"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by jfarhou on 2008-02-25
Hi all, I recently reinstalled ubuntu on my laptop and it works great, except for the fact that I can't watch videos in full screen w/ desktop effects enabled.  If I turn off desktop effects, I can watch full screen videos fine, but this means no cool animations/no awn.  Generally, when I try to watch full screen videos with desktop effects enabled my computer simply turns off (i'm guessing from overheating/overusing the cpu).  My computer is a year old and  handles 3D games quite well in windows, so I'm not really sure why it would perform so poorly in ubuntu.  Here are the specs:

HP Pavillion zd8000
Pentium 4 3.2 GHz
2 GB of RAM
ATI Radeon Mobility x600

I'm currently using the fglrx driver, and the output of lspci -n | grep is:

0300
01:00.0 0300: 1002:3150

Please, can someone help me make my laptop/cpu more efficient?

---

### Post by jfarhou on 2008-02-26
bump

---

### Post by Yellow Pasque on 2008-02-26
What video driver are you using? Type this is in a terminal:
```
fglrxinfo
```

> Please, can someone help me make my laptop/cpu more efficient?
The ATI driver itself is poor at accelerating 3D and your video card is very modest to begin with. Also, a P4 3.2 is an extremely hot chip that has no business being in a laptop. 

My recommendation is not to view full-screen video and use desktop effects at the same time because your cooling system is insufficient for this CPU load (it's the CPU's fault, you should've got an AMD).

---

### Post by jfarhou on 2008-02-26
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.0.6473 (8.37.6)

I realize it might not be the best graphics card, but in windows it runs WoW at a consistent 60fps,  I would just like to see some similar results with ubuntu if possible.

---

