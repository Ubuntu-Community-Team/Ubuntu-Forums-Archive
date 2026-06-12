---
title: "CDRom wont mount anything"
date: 2008-09-07
forum: General Help
---

### Post by iKougar on 2008-09-07
About 1 week ago I installed ubuntu with the livecd, now I cant load any cds. I was having some problems and wanted to do a clean install of ubuntu (im planning on switching to Xubuntu now) but it will not load my live cd, i have tried quite a few other cds and the only one that i did load was DSL,

```
alan@alan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4078c957-cf67-456d-8e2a-2fb67bf0f6f1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=fc067aa6-f58b-42b9-b1b6-229a63970327 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

idk if this could be causing this but i have been getting this error and i never tried loading a disk before i got this error - [http://ubuntuforums.org/showthread.php?p=5729117#post5729117](http://ubuntuforums.org/showthread.php?p=5729117#post5729117)

---

### Post by iKougar on 2008-09-07
I noticed how when ubuntu starts up it trys to do a scan and when it scans /dev/sda1 my computer freezes and i have to restart, maby ill have to fix that before my cdrom will start working again.

---

### Post by iKougar on 2008-09-07
> **iKougar said:**
> I noticed how when ubuntu starts up it trys to do a scan and when it scans /dev/sda1 my computer freezes and i have to restart, maby ill have to fix that before my cdrom will start working again.

I managed to fix this myself running fsck i think it was, cdrom still isnt working.

---

