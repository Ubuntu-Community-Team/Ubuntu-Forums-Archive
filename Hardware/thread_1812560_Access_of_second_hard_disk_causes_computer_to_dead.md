---
title: "Access of second hard disk causes computer to dead lock"
date: 2011-07-26
forum: Hardware
---

### Post by 16777216 on 2011-07-26
I have a 500 GiB sata drive as my primary drive with all of my OS partitions and a second 320 GiB pata (master) drive as a extra storage drive.

Grub is on the 500 Gib drive and Windows is using the 320 GiB rive's MBR for it's boot loader.  This is nice as I can reinstall Windows without worrying about grub.

The 320 GiB drive when accessed causes the computer to lockup hard.
The keyboard and mouse are unresponsive. The screen stops updating and all drive activity stops as well.

Under (*)Ubuntu, DSL, Parted Magic, Puppy, not only does the above happen but, sometimes the screen will blank then turn a light grey.

Under Windows XP/7/Vista the above happens as well but if the screen blanks it just stays blank.

I tried to re install Windows 7 but, it fails with an error along the lines of cannot install on this hardware.

I am currently using Hiren's Boot CD (HBCD) to see if I can find and fix the problem.

I have noticed that the low level drive scan tools on HDCD and linux's drive error scanner don't lockup.

Anyone have any thoughts?

---

