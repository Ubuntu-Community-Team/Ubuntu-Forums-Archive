---
title: "[SOLVED] Sound Stops Working After 8.04.1 Upgrade"
date: 2008-07-11
forum: Hardware
---

### Post by cmnorton on 2008-07-11
What files should I be looking at to understand better why my sound system stopped working after a 7.10 --> 8.04.1 upgrade. With 7.10, I had to add 

options snd-hda-intel model=thinkpad-t61p

to the end of /etc/modprobe.d/alsa-base

but the sound does not work with or without this line.

Any thoughts as to where to start?

tnx
cmn

Edit:
----------------------------------------
In KMix, both master and PCM have to be set.

---

