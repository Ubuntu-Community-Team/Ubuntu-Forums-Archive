---
title: "Asus A8N SLI RAID0 and Ubuntu"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by djgardyn on 2005-05-09
Hi everybody:
First of all, sorry for my english, spaniard!!!!
I've just bought an ASUS A8NSLI motherboard for AMD64, i installed Window$ XP with my 2 brand new SATA HD attached to Raid Controller of mainboard.
When getting to partitioning stage on Ubuntu instalation, doesn't recognize established RAID0. Imean, system recognize that there is a RAID0 hard installed but the only choice is to make a new RAID0 UNDER LINUX!!! or directly, format one of these two harddrives.
The questio: How can i install Ubuntu into a yet established RAID0+Window$ XP?
Maybe, hava i got to install Ubuntu on a empty RAID0 enviroment?

Please, tell me the right way to the path of perfection!!!!!!! :-k

---

### Post by coolmike890 on 2005-07-05
I have the same problem. Any solution yet?

---

### Post by Nachtengel on 2006-05-22
The problem you are experiencing is common with that motherboard, as it uses a fake RAID controller (a software RAID controller onboard).  This is a resource, but I have yet to get this to work in the AMD64 version.  Perhaps you'll be more successful with x86 builds.

[https://wiki.ubuntu.com/FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto")

Best of Luck!

---

