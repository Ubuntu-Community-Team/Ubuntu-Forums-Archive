---
title: "USB install in multiple different environments"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by funkyeah on 2009-09-14
Hey fellow nerds,

Has anyone installed Ubuntu 9.04 or 8.10 on a USB flash drive between very different systems?

Let me list the differences on the systems I'm trying to use with my prospective USB installation and my apprehension to even try this:

_System 1 & 2 (desktops):_
Intel E8500 / Q6700 (64 bit)
NVIDIA 9400 / 9800 GTs (1, 2 cards)
8 GB RAM (DDR2 800, 1600)

_System 3 (HP [Compaq] nc8230 laptop):_
Intel Pentium M 760 - 2 GHz (32 bit)
2 GB RAM (DDR2 533)
Radeon Mobility X600

So my question would be - can I use all the memory on all the boxes (aka use 32bit with PAE or memory mirroring) and get 3D acceleration using NVIDIA and ATI drivers when booting in different environments?

If I have to do some Xorg magic from the command line at boot this is acceptable (cp xorg.conf-nvidia[NUM] xorg.conf for each NVIDIA box, xorg.conf-ati for laptop), but I just don't know if it's that easy.

Can anyone give me some hope from personal experience before I start this adventure, haha?

---

