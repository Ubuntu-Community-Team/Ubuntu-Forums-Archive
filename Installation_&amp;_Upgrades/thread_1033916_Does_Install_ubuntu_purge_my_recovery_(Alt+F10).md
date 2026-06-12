---
title: "Does Install ubuntu purge my recovery (Alt+F10)"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by azwar on 2009-01-07
I have an acer aspire desktop. I want to install ubuntu on top of it. My acer desktop have 3 partition. 1=recovery partition, 2=winxp partition (ntfs), 3=fat partition.


Acer recovery environment can be activate by pressing Alt+F10 at boot time.

My question, if I install ubuntu on partition 2 winxp (ntfs) only, can I recover back my win xp OS just by pressing Alt+F10 at boot time.

---

### Post by lemming465 on 2009-01-09
If you use the recovery option, it would probably reset your disk to the factory shipped stated.  Any changes made in your XP partition would be lost; it might or might not also wipe out your FAT partition.

In your situation I'd do a WUBI install, where the Linux filesystem space is loopback mounted from a large blob allocated in your XP partition (C:\Ubuntu).  This avoids having to repartition your disk; all you need is 8+GB of free space on your C: drive (assuming that's what your winxp partition is designated).  It adds an Ubuntu boot option to your windows XP boot menu, and an uninstall option to windows add/remove programs.

---

### Post by Mark Phelps on 2009-01-09
As an added note, please see the Wubi subforum for specifics on Wuib installation and configuration.

Also, to use your NTFS partition, Wubi is the only option. The standard Ubuntu installer will not create an installation using an NTFS partition, it wants an Ext3-formatted partition.  Also, to do a standard installation, not only would you have to shrink your NTFS partition to make room for Ubuntu, you'd have to create an extended partition in that space, because you would need at last two partitions -- root and swap -- and you can't have more than four primary partitions on a single drive.

---

