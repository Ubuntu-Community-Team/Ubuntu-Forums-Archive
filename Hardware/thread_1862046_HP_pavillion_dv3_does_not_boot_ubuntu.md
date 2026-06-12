---
title: "HP pavillion dv3 does not boot ubuntu"
date: 2011-10-16
forum: Hardware
---

### Post by cloudslayer on 2011-10-16
Hi all,

I've been trying to install kubuntu (I tried both kubuntu 11.04 and 11.10) on a friend's laptop, but it not work: after trying to boot kubuntu it takes a while loading stuff (at least it seems that way as the dvd drive keeps on reading), but the screen remains black indefinately, even after nothing is read from the dvd drive...

The same problem also occurs when trying to load the last ubuntu version (11.10).

Does anyone know how I could try to diagnose this problem?

SYSTEM INFORMATION:
HP Pavillion dv3-450eb
Intel P6100 CPU
ATI Mobility Radeon HD 5470

---

### Post by 2F4U on 2011-10-16
I would suspect a problem with the graphics driver. You may wish to try to add nomodeset to the kernel boot parameters and see if you can get to the desktop.

---

