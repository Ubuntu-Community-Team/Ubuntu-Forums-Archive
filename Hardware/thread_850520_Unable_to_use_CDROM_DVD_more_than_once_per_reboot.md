---
title: "Unable to use CDROM DVD more than once per reboot"
date: 2008-07-05
forum: Hardware
---

### Post by shane25119 on 2008-07-05
Hi all

I have been using Ubuntu since way back in the day 2005-  And in that time I have never had a problem with my CDROM/DVDROM drives... albiet I didn't use them very much..

So now- I cannot use those drives.  If I reboot the system they're fine, but only for a short period.  Should I burn something with Basero... afterwards I cannot get any discs recognized, nor can I get Basero to open.  In really bad situations I cannot get applications like Totem to open or in rare cases I cannot get the file browser itself to open.

Now the odd thing is that my memory card reader... which connects to the computer via USB works just fine.  I have tried reinstalling, switching to xubuntu (same problem)- it's driving me slightly crazy.

Since I know folks will ask... here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=93a1fb8e-a1d4-442f-81d1-b31abce98e9e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=58b45b5d-990f-4865-b92f-e7a114823c4d /home           ext3    relatime        0       2
# /dev/sda2
UUID=d24ca083-b23e-4a58-b901-db399dedb08d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

