---
title: "Hard Disc switches between hda and sda"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by jspangler on 2007-06-09
Hi,

I'm relatively new at this, but i understand how to edit /etc/fstab to automount and all that. My problem is that sometimes my hard drive loads as hda, making my usb drive sda, but sometimes my hard disc loads as sda, making my usb drive sda.

What's going on exactly? And is there a way to fix it or to edit my fstab to account for this change?

Thanks for anybody's help !!:D

---

### Post by init1 on 2007-06-11
> **jspangler said:**
> Hi,

I'm relatively new at this, but i understand how to edit /etc/fstab to automount and all that. My problem is that sometimes my hard drive loads as hda, making my usb drive sda, but sometimes my hard disc loads as sda, making my usb drive sda.

What's going on exactly? And is there a way to fix it or to edit my fstab to account for this change?

Thanks for anybody's help !!:D
Weird, I didn't know that was possible. Do a fdisk -l and give me the results.

---

### Post by jspangler on 2007-06-12
OK, here it is:

sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5384    43246948+   7  HPFS/NTFS
/dev/sda2            5385        7210    14667345   83  Linux
/dev/sda3            7211        7296      690795    f  W95 Ext'd (LBA)
/dev/sda5            7211        7296      690763+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       38276   307443906    7  HPFS/NTFS
/dev/sdb2           38277       38913     5116702+   f  W95 Ext'd (LBA)
/dev/sdb5           38277       38913     5116671    b  W95 FAT32

---

### Post by bunted on 2007-06-12
I had a similar problem, but I think it was the cause of kernel updates.  I would just update my fstab according to how the drives were assigned.  I haven't had that happen in a few weeks.

---

### Post by jspangler on 2007-06-12
Hmm, hopefully my drives will stay put then :-)

---

### Post by markoloka on 2007-06-12
Kernel update errors:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314)

---

