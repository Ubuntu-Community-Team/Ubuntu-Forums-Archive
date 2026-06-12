---
title: "fsck.ext3: Unable to resolve 'UUID="
date: 2008-05-06
forum: Hardware
---

### Post by VMC on 2008-05-06
I'm using ubuntu 8.04 Harty Heron

I get the following error with command 'fsck'. I have searched and read various solutions. It may be in the fstab, but I can't find it. Here are my outputs for the following commands:

================FSCK==================
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=[COLOR="Blue"]d8533154-cef1-4cce-a823-9f3f74aab65b[/COLOR]'
================FSTAB=================
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=[COLOR="Blue"]d8533154-cef1-4cce-a823-9f3f74aab65b[/COLOR] /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0703bda2-3d0b-42e5-9d49-5c2634a4bd53 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
================FDISK=================
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3200    25703968+  83  Linux
/dev/sda2            3201        3576     3020220    5  Extended
/dev/sda5            3201        3576     3020188+  82  Linux swap / Solaris
=================vol_id /dev/sda1=====
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=[COLOR="Blue"]d8533154-cef1-4cce-a823-9f3f74aab65b[/COLOR]
ID_FS_UUID_ENC=d8533154-cef1-4cce-a823-9f3f74aab65b
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
======================================

Any help would be appreciated, thanks.

---

### Post by Andre-D on 2008-05-09
same problem here.. did you find a solution ?
Mine was caused by me removing an partition, and enlardging EXT3

i fixed GRUB, checked fstab and averything seems ok, all you posted, is "OK" here too.

fsck gives same error as you have
"sudo fsck" does not give error, but warns about not repairing an unmounted file system.

Did you find a solution ?

---

