---
title: "hard drive weirdness"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by kamui_18 on 2007-06-09
I have 4 different hard drives on my pc, all of them are on ntfs format (I've got winxp on dual boot). I already have ntfs-3g installed and it is not able to mount the following drives:

/dev/sdb2 (SATA)
/dev/sdb1 (SATA)
/dev/sdb4 (IDE)

When I log in as root, it shows that the drives are read only. I've tried rebooting in to windows about 2 times and booting back to ubuntu to no avail.

---

### Post by red_five on 2007-06-10
First, if you have 4 different physical drives, then they'll be sda, sdb, sdc, and sdd, not sdb1, sdb2, and so on. The numbers indicate partitions on a single physical device, the changing 3rd letter (sdX) indicates the actual physical device. If each drive has a single partition, then you'll have (for instance) sda1, sdb1, sdc1, and sdd1.

The fact that you're getting everything mounted read-only may be related to this. If you use GNOME, install gparted and use it to check the device names and partition numbers, then use those in your mount commands or /etc/fstab.

---

