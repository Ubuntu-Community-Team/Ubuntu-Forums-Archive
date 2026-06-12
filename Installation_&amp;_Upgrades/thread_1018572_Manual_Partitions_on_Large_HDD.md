---
title: "Manual Partitions on Large HDD"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by CRJeepin on 2008-12-22
Hello all,
Been a while since I've run Ubuntu and tried installing 8.10 onto an older computer yesterday but had a problem with GRUB (error 18 ) because the BIOS doesn't support the 160gb hdd that is installed.

I did some reading and ended up trying to use [this walkthrough](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall) to create a boot partition but kept having problems, so I gave up for now and threw XP back on (wife needs computer while I'm at work).  I believe the issue was that 8.10 appears to use UUID's in the menu.lst file and I'm not sure I was able to get them set up right.

What I would like to do is a clean install with manual partitions.  I tried that last night too, but ran into an error GParted that didn't seem to make sense.  Can't recall exactly what it was but it didn't think I had a root partition, even though I did.

**Could someone give advice on these partitions?**

_Here are my proposed partitions_
1.  100 mb - /boot
2.  120 gb - NTFS (xp..for now)
3.  20 gb - /  (root)
4.  2 gb - swap

_Questions:_
1.  Can all (/boot, /, swap) be "ext3" type?
2.  During install, will Ubuntu 8.10 automatically put the correct GRUB files in /boot?
3.  Do I need to sub-divide the "/" directory further or will the installer do it?

Thanks for the help all.

CR

---

### Post by albandy on 2008-12-22
/boot and / should be ext3, reiser, xfs ...
/swap should be swap

You don't need to subdivide "/" but is recomended. Imagine you want to reinstall the o.s. If you previously defined a /home partition you can reinstall without erasing the /home files

---

