---
title: "mounting problem"
date: 2008-07-31
forum: General Help
---

### Post by BoneSaw on 2008-07-31
okay so i have been having trouble with my usb ports. if the system locks up or i try and write too much at once, it disconnects my external hard drive. thats not what this is about. sometimes when this happens instead of mounting at /media/disk (like it normally does) it mounts at /media/disk-1 which messes up file paths for things like amarok and deluge.

so when it did this today, i clicked options and foolishly tried to fix it by changing the mount point through there to /media/disk, and now of course it wont mount at all. at first it gave an error about having a newline or improper character. then i tried editing fstab to the following

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78d5c908-2192-4591-8258-0b4a755a8b9f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=53c8c315-ad15-4101-91c3-2db46a50ffce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=811da631-ae24-4080-bc5f-5de836a6e670  /boot ext3 defaults 0 0
/dev/sdb        /media/disk      ext3    defaults           0       0
```

from the original
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78d5c908-2192-4591-8258-0b4a755a8b9f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=53c8c315-ad15-4101-91c3-2db46a50ffce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=811da631-ae24-4080-bc5f-5de836a6e670  /boot ext3 defaults 0 0
```

at first i had the filesystem for /dev/sdb set to auto, but it said i needed to specify the filesystem so i set it to ext3 and when i did mount -a it gave me this error.

"mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

it is ext3 so im at a loss.
](*,)

---

### Post by Tim Sharitt on 2008-07-31
Try changing /dev/sdb to /dev/sdb1.

---

### Post by BoneSaw on 2008-07-31
haha thanks that did it

---

