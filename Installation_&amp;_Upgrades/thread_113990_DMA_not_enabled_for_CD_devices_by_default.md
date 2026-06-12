---
title: "DMA not enabled for CD devices by default"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2006-01-07
When installing 5.04 or 5.10 on a desktop PC with IDE devices (1 disk, 1 CDROM, 1 CD Writer) I observe that the disk is put into DMA mode, while the CD devices are not.

The installation procedure asks, at least in expert mode:
[INDENT]Tune CD-ROM with hdparm ?[/INDENT]
and entering a "-d1" indeed puts at least the installation CD device into DMA mode.
I have to edit hdparm.conf to get the second CD device into DMA.

Can somebody explain this behaviour ? Why is DMA on by default for disks, but not for the CD devices ?

---

### Post by bored2k on 2006-01-07
Some old hardware (mainly cd/dvd devices) would have serious issues with hdparm (as serious as permanently damaging them). For this reason, they're not on by default. It's similar to Ubuntu using the 386 kernel by default. If we had the 686 by default, people with old hardware would get a bad experience from UBuntu.

[http://www.ubuntuforums.org/showpost.php?p=636389&postcount=3](http://www.ubuntuforums.org/showpost.php?p=636389&postcount=3)

---

