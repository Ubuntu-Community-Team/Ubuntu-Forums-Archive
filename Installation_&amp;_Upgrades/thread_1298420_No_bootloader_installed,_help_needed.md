---
title: "No bootloader installed, help needed"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by ska8tdude on 2009-10-22
I just reformatted my laptop with the retail version of Windows 7 today, and decided to dual-boot with Ubuntu 9.10 beta. However, during the alternate CD install it got to the grub2 install and would not continue, the pick next step screen kept popping up. So I stupidly decided to continue without a bootloader, is there anyway for me to install grub2 from the 9.10 Live CD? I'm not very well versed in terminal commands and the like, so easy to follow directions would be incredibly helpful. 

I've managed to dual-boot Ubuntu a few times before without any issues on my RAID 0 setup, but I have no idea what to do with this problem.

---

### Post by dstew on 2009-10-23
Is your laptop currently set up with a RAID of some type?

See this [page about grub2]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing"), the part "If you messed up" has instructions on how to re-install grub2. If you have a RAID, I am not sure it will work right, but that is as much as I know. Maybe grub2 works with RAIDs, I know grub 0.97 did not.

---

