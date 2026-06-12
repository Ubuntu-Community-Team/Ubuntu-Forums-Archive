---
title: "Dual booting Win2k/Edubuntu..."
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by aleXL on 2005-12-13
Dual booting is working... mostly...

However, after rebooting from Edubuntu, Win2k will only boot properly on the second attempt... the first attempt results in a hang on the Win2k splach screen, where the blue blobs only get halfway...

It's as if Edubuntu is doing something to Win2k's innards...

I've #d the reference to hda1 partition (ntfs) in fstab, to see if that helps, but to no avail...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
**# /dev/hda1       /media/hda1     ntfs    defaults        0       0**
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Any ideas?

---

