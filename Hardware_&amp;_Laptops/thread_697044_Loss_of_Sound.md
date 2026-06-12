---
title: "Loss of Sound"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by elihu2 on 2008-02-14
Toshiba A25 laptop, dual-booting XP and Kubuntu 7.10. While playing a
DVD yesterday, the sound stopped. 

The sound on the XP side is OK. I booted Knoppix 5.0 and sound is normal
there also. Knoppix says the soundcard is Ali Corp. M5451 and driver is
trident. 

Apparently, the hardware is intact. Perhaps there is a driver issue of
some sort.

In times past, I've been able to use sndconfig to reload an errant sound
card. Kubuntu does not recognize that command. Any suggestions?

---

### Post by elihu2 on 2008-02-15
Found the problem. I had PCM muted in the mixer window, probably as a result of hitting a hotkey.

---

