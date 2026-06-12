---
title: "Atheros 5007EG finally working out of the box"
date: 2009-01-28
forum: Hardware
---

### Post by absolut1983 on 2009-01-28
Lads,

  My wireless card, the bloody Atheros 5007EG, is now working just out of the box, no Windows drivers.

  Right after I installed today's update for the 9.04 version and restarted the system, checked the network status and saw all the available wireless connections. And it works like a charm.

  I can barely believe it. Nearly two years struggling with this annoying piece of hardware. Step by step we'll sort out all the issues that pester our Linux experience.

  What a bliss!

---

### Post by marianomocoroa on 2009-01-28
> **absolut1983 said:**
> Lads,

  My wireless card, the bloody Atheros 5007EG, is now working just out of the box, no Windows drivers.



In intrepid you no need windows drivers, only do 

sudo apt-get install linux-backports-modules-$(uname -r) 

and reboot-

---

### Post by absolut1983 on 2009-01-28
Yes, but that is a workaround anyway, isn't it?

   How could the average Joe possibly know this without spending a couple of hours researching?

   The card now works from the moment you finish the installation, no terminal, no extra downloads. It just works, like everything else should.

---

