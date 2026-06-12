---
title: "Ubuntu partition too small on Aspire One D250"
date: 2009-07-28
forum: Hardware
---

### Post by markiangooley on 2009-07-28
The Upgrade Manager says I don't have enough room on the disk to install upgrades... which is no surprise because the default installation created a 2 Gb partition on the 160 Gb disk originally taken up by XP.  I can understand a 2 Gb partition on a 4 or 8 Gb SSD, but...

I'd really appreciate a suggestion for an easy way to enlarge the Ubuntu partition.  I plan to use Ubuntu Network Remix (which so far I really like) much more than I use XP, and I'd like most of the drive to be Ubuntu.  Reinstallation would be okay as I haven't added much yet other than Xchat.

Thanks!
Mark.

---

### Post by mikewhatever on 2009-07-28
There is no such thing as default installation. Something must have gone wrong during partitioning, and an aducated guess suggests you may have got the mount points wrong, mounting the swap partition to be root. Can you post the output of the following command from Applications->Accessories->Terminal to ascertain there is no unused partition floating around.

**sudo fdisk -l**

---

### Post by markiangooley on 2009-07-28
Here goes:

gooley@bluebottle:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a0d38ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  12  Compaq diagnostics
/dev/sda2   *         915       19132   146329432    7  HPFS/NTFS
/dev/sda3           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris

gooley@bluebottle:~$

Thanks.

---

### Post by mikewhatever on 2009-07-29
Right, so the root is quite small indeed. You can resize it while running from usb, and, either reinstalling and repartitioning in the process, or using a Partition Management program that should be under System->Preferences. You have to be running from USB to ensure the root partition is unmounted. Reinstalling is also advisable, because when you resize a partition, its UUID changes, and you then need to manually change it in several config files. If you resize and reinstall, the installer will take care of UUIDs.

---

### Post by markiangooley on 2009-07-29
Thanks.  I reinstalled from the USB key, deleted the old linux and linux swap partitions, reduced the Windows system to 70 Gb, made new 80-ish and 2-ish GB root and swap, and everything seems to work fine.

---

