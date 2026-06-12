---
title: "Sata  very slow 8.04"
date: 2008-09-11
forum: Hardware
---

### Post by chadeldridge on 2008-09-11
Just like the title says, SATA is very very slow 20mb at fastest.  I have tried a lot of tweaks listed in the boards, but no luck.

I can actually copy and paste files from my sda to my external hard drive faster than I can from folder to folder on the sda.


Let me know what info is needed and I will provide it.

```
 uname -a 
Linux celdridge-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```


fstab```
proc /proc proc defaults 0 0
UUID=f550dc57-40f8-466c-81f8-391cbc7d32cf / ext3 defaults,errors=remount-ro,data=writeback,noatime,nodiratime,nobh,commit=100     0     1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0


```

---

### Post by thepizzaman on 2008-09-11
ok this may be a stupid answer but did you remove the jumper that limits the speed to the drive?

---

