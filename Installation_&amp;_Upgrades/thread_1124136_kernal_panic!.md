---
title: "kernal panic!"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by mephostophilis on 2009-04-13
I'm tying to install ubuntu 64 bit version on my work computer (HP Compaq dc7700c) but when I boot from the unbuntu CD I get the message bellow. Note the unbuntu CD works in other computers and the MD5 Sums check is  ok.




[    0.000000] initrd extends beyond end of memory (0x7ef8fd58 > 0x7e000000)
[    0.000000] disabling initrd
[    0.461784] Kernal panic - not syncing: VFC: Unable to  mount root fs on unknown-block(8,1)

---

### Post by rage9 on 2009-04-13
Guess the obvious question is:  does your processor have 64 bit functionality?  Have you tried the 32 bit version?

---

### Post by bgerlich on 2009-04-13
How much RAM do ou have ? Try adding the parameter mem=(amount of ram in MB)MB to your boot options.

---

