---
title: "Automatic Mount with Read Write"
date: 2008-10-31
forum: General Help
---

### Post by Deathray on 2008-10-31
This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8eff7a49-369b-4c02-b3ff-f7a6f7d89cb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=96013f26-b3b0-4f06-9420-67ec5faf892b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 ntfs ro,user,fmask=0111,dmask=0000 0 0
```
I would like /dev/sda1 and /dev/sda2 to be mounted with read and write permissions for my current user. It auto-mounts now but without write permissions.  How do I proceed?
Thanks in advance! (:
(Ubuntu 8.10)

---

### Post by tagbre on 2008-10-31
adjust the lines of those devices after 'ntfs' to look like this:

```
# /dev/sda7
UUID=B64C59BA4C597659 /mnt/sda7     	ntfs    defaults,umask=007,gid=46 0       1
```

---

