---
title: "ASUS A8N-SLI - 1 SATA HDD - Boot Problems"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by sixstorm on 2007-04-18
I've looked all around the board and nobody has had the problem I'm having.  I have:

AMD Athlon 3200+
ASUS A8N-SLI Premium
1 GB RAM
80GB SATA Western Digital HDD
Zalman 600-watt PSU
EVGA NVIDIA 7600GT Vid Card

Ubuntu 6.10 installs just fine, can see the SATA drive and all, but when you go to boot the OS, the splash screeen comes up and it hangs.  I thought to myself that maybe it was kinda like with Windows where you have to have the SATA driver disk in order for it to install properly but I ruled it out.  I used to have Windows Vista and XP on there last week but I wanted to convert it over to a Ubuntu Media Server.  Any suggestions?

---

### Post by sixstorm on 2007-04-18
Alright, I solved my own problem.  Where Windows just has to have your SATA drive connected via SATA_RAID port, Ubuntu does not.  I hooked the drive up to the regular SATA port and it worked just fine.  I would say it's a little slow on startup but it works fine as I am typing this from Ubuntu now.  Now to update and all that fun jazz.

---

