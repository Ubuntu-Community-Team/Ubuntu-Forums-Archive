---
title: "External Hard Drive Won't Mount"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by nSTER on 2007-04-26
My external hard drive won't mount when I click on it. It would give me this error:

Unable to mount volume 'External HD'

Volume is scheduled for check. Please boot into Windows TWICE, or use the force mount option.

I tried booting into windows twice and trying to force command but it doesn't work.

The external hard drive is a ntfs hard drive on usb.

I managed to access it a while back but it wouldn't let me access any of the data.

Here is my fdisk output the drive is the sda1:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2289    18386361    7  HPFS/NTFS
/dev/hda2            2290        8494    49841662+  83  Linux
/dev/hda3            8495        8764     2168775    f  W95 Ext'd (LBA)
/dev/hda4            8765        9729     7751331    c  W95 FAT32 (LBA)
/dev/hda5            8495        8764     2168743+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Thanks.

---

### Post by XTREEM|RAGE on 2007-04-26
you need to remove it from windows "safely remove hardware" from the taskbar .
That helped for me!

---

