---
title: "[SOLVED] Trouble keeping an external hard drive mounted (after upgrading to Gutsy)"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by bswilson on 2007-10-20
I recently performed a dist-upgrade from Feisty to Gutsy, which went very smoothly, no problem.

During the upgrade, I unplugged my 1GB Maxtor USB 2.0 external hard drive, which contains all my backed up home directory information, etc.

After the upgrade to Gutsy, I plugged my drive back in, and it automatically mounted no problem (as I had expected).

My problem is that the desktop icon (and associated mount point) randomly disappears!  It seems to always dismount when I exit from Amarok, although I do not have Amarok configured to manage this device.

I am unsure of where to start troubleshooting this problem.  Can someone guide me, please?

Here is my /etc/fstab file for reference.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=823f48dd-d326-41fc-87d4-f5e5d52773cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=eaa7293e-a116-4c5f-8f5f-44eabd4cdd04 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# ipod
/dev/sdb1       /media/ipod     vfat    user,noauto,umask=000   0       0
/dev/sdb1       /media/ipod     vfat    nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8  0      0
```

My USB drive doesn't have an entry, and I am not sure why I have 2 mount point entries for my ipod, I only have 1 of them.  I suspect the upgrade added one entry.

---

### Post by bswilson on 2007-10-29
Well, I'm sorry to say that the way I fixed this was that I switched from Amarok to Rhythmbox.  :(

---

