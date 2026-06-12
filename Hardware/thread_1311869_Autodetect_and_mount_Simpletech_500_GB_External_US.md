---
title: "Autodetect and mount Simpletech 500 GB External USB Drive on Startup"
date: 2009-11-02
forum: Hardware
---

### Post by inkhorn on 2009-11-02
Hi all,

I've been having a problem that has occurred both in Ubuntu 9.04 and now 9.10.  Ubuntu doesn't seem to reliably detect and mount my Simpletech 500 GB external USB drive on startup.  For some reason, I have to take out the power cable, take out the usb cable, then put the power and usb cable back in for it to detect and automount it after I've started up.  Is this an Ubuntu or Simpletech problem?  Here are the results from typing "sudo fdisk -l" before and after my system has detected the drive (aka, before and after I took out and power and put back power and USB):

```
inkhorn@inkhorn-laptop:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96dfc149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         191     1534176   82  Linux swap / Solaris
/dev/sda2   *         192       13992   110851562+   7  HPFS/NTFS
/dev/sda3           13993       19457    43897612+   5  Extended
/dev/sda5           13993       19457    43897581   83  Linux
inkhorn@inkhorn-laptop:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96dfc149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         191     1534176   82  Linux swap / Solaris
/dev/sda2   *         192       13992   110851562+   7  HPFS/NTFS
/dev/sda3           13993       19457    43897612+   5  Extended
/dev/sda5           13993       19457    43897581   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4782494a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

Should I just take the drive back?  When it's up and running it gives me no problems.  It's just getting it up and running which is the annoying problem!!

Thanks,
Inkhorn

---

