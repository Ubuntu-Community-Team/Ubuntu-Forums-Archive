---
title: "Hardware RAID"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by neoncode on 2007-09-29
Currently I have 4 250GB drives in software Raid 5 for my /home and a 150GB WD Raptor for my Linux root partition and my Windows partition. Thing is, windows is running out of space. So I want to get another Raptor drive, setup a 2nd partition of windows on that(not in raid) and Raid-1 the system partition while I'm at it. Thing is I've run out of SATA-II ports on my motherboard.

So I was thinking I might as well just get a 4-Port Hardware RAID card and plug my 4 250's into that and setup hardware RAID 5 to get better performance than my mdadm software RAID I'm currently using. Does anyone know of any good, cheap cards that offer good performance with RAID 5 and support for 4 SATA-II drives? Oh and be compatible with Linux of coarse. Compatibility with Windows Vista isn't needed, but isn't a negative point if it has it.

---

### Post by ShadowVlican on 2007-09-30
check out some of their cards:
[http://www.highpoint-tech.com/](http://www.highpoint-tech.com/)

i have the RocketRAID 2320 and it works fine in windows... but it's an 8 port card

---

### Post by neoncode on 2007-10-04
These cards function fine under Linux I assume? And if I have more than four ports on a RAID card could I plug all 6 hard drives into it (the 4 250's and the 2 150's) and get my RAID 5 over the 250's and use the last 20GB or so from each of the 150's under RAID 1 for my root directory. And make it leave the rest of the two 150's as just 2 unformated bits to put windows over two seperate partions?

---

