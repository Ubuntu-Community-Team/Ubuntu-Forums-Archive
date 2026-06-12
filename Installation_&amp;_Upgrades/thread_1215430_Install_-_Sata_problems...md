---
title: "Install - Sata problems???.."
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by darksong on 2009-07-17
Hi all, i am sorry i think i made i similar thread before but i forgot to bookmark it before my holiday and have lost it :S (Can't find it through search etc).

When trying to install Ubuntu (or any other Linux) fails to find my Sata hard drive. It doesn't recognize it. On the partitioning page it shows blank.

My specs are: 

Foxconn SKT939
Maxtor STM3250820AS 250GB
AMD Athlon 64 X2 4200 Dual-Core

Any help would be much appreciated... :P

---

### Post by dstew on 2009-07-17
Sometimes, the Live CD kernel lacks the software to detect drives in certain systems. Older kernel versions sometimes work. You can try an older version Live CD, and once installed, upgrade. For example, install 8.10, then use update manager to upgrade to 9.04, if that is what you want. Or, you could just install an older version and be content with that (I am).

Another option is to use the Alternate Install CD. It uses a different installation interface (text-based) that may work better with your hardware. It installs the same Ubuntu desktop as the Live CD.

Once you have the Ubuntu system installed, it is much more likely to work with your disks, because the installation process adds a lot of capability to the kernel. The barrier is getting the installation disk to see your disk.

If you can't get ANY linux kernel to see the disk, you might have a BIOS setting that needs to be changed. For example, if it is set for RAID, you might change it. Also, kernel parameters can be tried. For example, the kernel parameter **pci=nomsi** fixed [a similar problem]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492") (different hardware though -- don't know what it will take to fix yours).

---

### Post by darksong on 2009-07-17
Ok, thanks for the advice, i will try it out and get back on how it worked :P..

---

