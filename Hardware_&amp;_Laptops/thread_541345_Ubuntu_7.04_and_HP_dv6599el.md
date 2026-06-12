---
title: "Ubuntu 7.04 and HP dv6599el"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by elegos on 2007-09-02
Hi there!

I've bought a new laptop - the HP Pavilion DV6599el (the white special edition one)... I've tried starting up the liveCD of ubuntu, but it said something about tty... here is the error:

/bin/sh: can't access tty; job control turned off

well... I've 'fixed' it writing

modprobe piix
exit


ok, ubuntu loaded, but @ the login screen, the screen became black... so I downloaded the alternate CD and installed ubuntu with no problems... but (obviously) when I started it... black screen @ the login screen... sigh sob... I've pressed CTRL+ALT+F1 and did all the updates and installed the restricted nvidia drivers... NOTHING!!! dpkg-reconfigure xserver-xorg.... NOTHING!!!

Please help me!

Model: DV6599EL
CPU:  Core 2 Duo T7300
RAM: SDRAM DDR2  2048MB (2x 1024MB)
HD: SATA 160 GB
Display: LCD WXGA 15,4" BrightView 1280x800 pixel
GPU: GeForce Go 8400M (128MB ->  895MB TurboCache)

P.S.
This laptop is my father's one... I can access to it only in the evening... If only I could install linux on it, my father could learn linux!!! (When I met it, I loved it!)

Thank you!

---

