---
title: "Install of Intrepid 64-bit with nVidia 8600GT freezes on starting X"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by sprocket12 on 2009-03-07
Hi all.  I searched but didn't seem to find anything relevant.  As the subject states, the X server freezes immediately after starting before the install begins.  I have actually tried 32-bit and 64-bit.  I even went back to an 8.04 32-bit CD.  Everyone had the same problem.  Weird thing is I have had 8.04 and upgraded to 8.10 on this box in the past.

Anyway, I am posting this for others who may have a similar issue.  I found that by adding the option: 'xforcevesa' to the kernel options at boot, I can do the install.  I am assuming that I can install my restricted nVidia driver after the installation completes.

---

