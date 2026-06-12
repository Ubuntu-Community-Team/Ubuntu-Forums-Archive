---
title: "dual boot xp/xubuntu xp autochk missing error"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by midwestnewbie on 2009-01-02
Hello, A quick intro. I have been using xubuntu off live cd and decided to install on my xp system. So i used partition magic to make some partitions, and now i have xubuntu installed in what i believe is the first partition. and when i reboot and choose xp from grub menu it goes to xp screen and then to blue screen and says autochk missing, skipping autocheck, and continues to loop until i let it go into xubuntu, which works fine. So, been lurkin and learned a lil bit about using terminal and now need to figure out how to point grub to the right location to boot to xp. Any help would be greatly appreciated.

here is my sudo fdisk -l
--------------------------------------------------

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1167f4d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3434       44557   330324185   17  Hidden HPFS/NTFS
/dev/sda2              40        3433    27262273+  83  Linux
/dev/sda3           44558       60801   130479930    f  W95 Ext'd (LBA)
/dev/sda5           57806       60801    24065338+   7  HPFS/NTFS
/dev/sda6           44558       57261   102044817   83  Linux
/dev/sda7           57262       57805     4369648+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)
-----------------------------------------------------------------------

Thanks in advance!

---

### Post by Partyboi2 on 2009-01-03
Try unhiding your sda1 partition with partition magic or
[http://www.pchell.com/support/autochknotfound.shtml](http://www.pchell.com/support/autochknotfound.shtml)

---

