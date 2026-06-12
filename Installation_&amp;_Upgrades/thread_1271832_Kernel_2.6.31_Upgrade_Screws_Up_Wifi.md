---
title: "Kernel 2.6.31 Upgrade Screws Up Wifi?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by snowman4839 on 2009-09-21
I just compiled kernel 2.6.31 overnight and installed it in about 15 minutes this morning. During the install I double checked to make sure it would compile with my laptop's Atheros 5007EG driver so it would install the ath5k driver. I booted into the new kernel this morning and it didn't recognize my wireless!! I had a similar problem with 2.6.28-13 because 2.6.28-11 would recognize it and work somewhat (it works off and on) but 2.6.28-13, it didn't recognize my wireless card at all and same thing with 2.6.31. Does it have ath5k blacklisted by default or something? Why isn't it recognizing it?? iwconfig and ifconfig only turn up loopback, ethernet, and pan0 (what is that?)

---

