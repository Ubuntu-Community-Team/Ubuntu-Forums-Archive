---
title: "read fat32 partition?"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by desperatecoffee on 2005-02-08
i have my hard disk partitioned into an ntfs for win xp, a swap, an ext3 for ubuntu, and a fat32 that both windows and linux can access. but the fat32 drive doesn't show  up in ubuntu. it is not in /etc/fstab, which i will include here for your reading pleasure ^_^

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0

i previously had mepis installed on the ext3, which read the fat32 fine on /dev/hda4. so do i have to install a driver, or just edit fstab, or what? thanks, any help would be greatly appreciated.

---

### Post by Buffalo Soldier on 2005-02-08
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by desperatecoffee on 2005-02-08
brilliant. thanks.

---

