---
title: "Please Make This Simple"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by joeinazyes on 2007-08-05
I have two internal hard disks, hda and hdb.  hdb is FAT32.  I want it to automatically mount on startup with read and write permissions.  PLEASE do not point me to some other forum posting, I think I have been to them all.  PLEASE DO read my fstab file posted below and display the correct entry for boot up that will accomplish what I want.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3c00a505-4c9f-4205-a303-c44314fc8bf0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=00c52fa0-37cc-4083-8bea-6bb3ac348429 none            swap    sw              0       0
/dev/hdb	/media/hdb	auto,users,async,exec,dev,suid,rw,mode=777,umask=000
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thank you.

---

### Post by merlinus on 2007-08-05
Try changing:

/dev/hdb    /media/hdb    auto,users,async,exec,dev,suid,rw,mode=777,umask=0  00

/dev/hdb /media/hdb -t vfat -o umask=000

You might also post results of:

```

sudo fdisk -l

```Because you will probably be wanting to mount it as hdb1 rather than hdb.

-merlin

---

### Post by kerry_s on 2007-08-05
/dev/hdb /media/hdb auto,users,async,exec,dev,suid,rw,mode=777,umask=0 00
to
/dev/hdb /media/hdb  auto  defaults,user  0  0

you just need to space it right

dev (space) mountpoint (space) type of file, auto will take care of that (space) settings, no need to get complicated (space) should it be checked, 0=no 1=yes, it should not be checked.

---

