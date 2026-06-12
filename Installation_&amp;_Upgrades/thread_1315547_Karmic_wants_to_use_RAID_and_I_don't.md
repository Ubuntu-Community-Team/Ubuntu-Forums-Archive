---
title: "Karmic wants to use RAID and I don't"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by smudge12b on 2009-11-05
I'm trying to do a clean install of Karmic. It will be a dual boot with Windows XP on one HD and Karmic on the other. When I get to the partition part of the install it is forcing me to mirror the hard disks and not giving me a choice of either disk. I tried disconnecting the Windows HDD but then Grub would not find it when I plugged it back in (I did rerun Grub from the LiveCD and also edited menu.lst). The RAID is disabled in BIOS and a reinstall of Jaunty has no such problem. I have reisntalled Jaunty for the time being but would like to try the upgrade.
 
I have an ECS C51GM-M motherboard with 3.8Ghz AM2 processor, 2 Samsung 500Gb HDDs

---

### Post by Shazaam on 2009-11-05
During installation did you try "Manual" (custom?) partitioning instead of "Guided"?

---

### Post by smudge12b on 2009-11-05
I used manual to make sure I didn't lose the windows partition. I've kind of got round the problem, I reloaded Jaunty and then upgraded it. Everything is work fine, I guess I'll try the clean install another time :)

---

