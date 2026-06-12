---
title: "Hard Disk Crashed"
date: 2009-08-08
forum: Hardware
---

### Post by crazydog on 2009-08-08
My secondary hard-disk crashed after an electricity failure.
Any help would be appreciated

my /var/log/fsck/checkfs output is
[INDENT]Log of fsck -C3 -R -A -a 
Sat Aug  8 07:17:53 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: No such file or directory while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Aug  8 07:17:53 2009
----------------
[/INDENT]

and My /etc/fstab is:
[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3381d836-2e9b-4cd0-8131-f537d49eebdb /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=fa5c1a96-686b-4fed-847d-9f1694f06465 none            swap    sw              0       0
# /dev/sdb1
/dev/sdb1       /users        ext3    defaults,relatime 0 2
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/INDENT]

---

### Post by crazydog on 2009-08-08
some extra info,
trying to mount /dev/sdb1 I get:

mount: special device /dev/sdb1 does not exist
:confused:

---

