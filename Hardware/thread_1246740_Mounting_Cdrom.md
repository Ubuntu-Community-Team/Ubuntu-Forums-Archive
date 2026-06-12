---
title: "Mounting Cdrom"
date: 2009-08-22
forum: Hardware
---

### Post by radar56 on 2009-08-22
I just installed ubuntu and for a while the cdrom was mounting fine, now it won't mount.   

adam@adam-laptop:~$ mount /dev/scd0
mount: special device /dev/scd0 does not exist

FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ee88e457-8e9f-4e73-a6b0-fe8213446944 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=90f0c13c-2639-4ebf-82c7-0987c2587088 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto user,noauto,exec 0       0

Thank You

-adam

---

### Post by khelben1979 on 2009-08-22
Maybe there is something wrong with the cd-r discs you are trying out? Give us some information about the drive.

---

### Post by radar56 on 2009-08-22
It works now after I had it shut down all night.  I guess I will just see how it goes.

---

