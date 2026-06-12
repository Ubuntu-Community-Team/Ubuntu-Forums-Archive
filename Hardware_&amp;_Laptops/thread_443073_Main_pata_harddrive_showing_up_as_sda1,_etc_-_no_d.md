---
title: "Main pata harddrive showing up as sda1, etc - no /dev/hda* - Feisty"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Portable_Jim on 2007-05-14
I have just upgraded to Feisty. I have noticed that my main PATA hard drives are at /dev/sda1, /dev/sda2, etc. Under Edgy they were hda1, hda2, etc.

ls -lF /dev/disk/by-path/ reveals:
```
lrwxrwxrwx 1 root root  9 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:0:0-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:1:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:1:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-0:0:1:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2007-05-15 06:14 pci-0000:00:1f.1-scsi-1:0:0:0 -> ../../scd0
lrwxrwxrwx 1 root root  9 2007-05-14 20:17 pci-0000:01:09.2-usb-0:4:1.0-scsi-0:0:0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 2007-05-14 20:17 pci-0000:01:09.2-usb-0:4:1.0-scsi-0:0:0:0-part1 -> ../../sdc1
```cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=6a28f493-0aa4-4e82-89f4-030b178c2354 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=fe156e1c-e143-4075-bd27-0dec3383064f /media/oldhome           ext3    defaults        0       2
# /dev/hda1
UUID=5ADCDFFFDCDFD2FD /media/Win_XP   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=6AB82AC1B82A8B9F /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4   swap         swap    defaults              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```ls /dev/hd*:
```
ls: /dev/hd*: No such file or directory
```How do i restore them back to hda1, hda2, etc?

---

### Post by hartz on 2007-05-14
This is due to Feisty using the new, much-improved libata stuff.

Why would you want it to use the old /dev/hda?  that is just *so* 2.6.16 <grin>

---

### Post by Portable_Jim on 2007-05-14
> **hartz3 said:**
> This is due to Feisty using the new, much-improved libata stuff.

Why would you want it to use the old /dev/hda?  that is just *so* 2.6.16 <grin>
I discovered that after a bit more searching. I saw
[http://ubuntuforums.org/showthread.php?t=419730](http://ubuntuforums.org/showthread.php?t=419730)
and
[http://ubuntuforums.org/showthread.php?t=422336](http://ubuntuforums.org/showthread.php?t=422336)

---

