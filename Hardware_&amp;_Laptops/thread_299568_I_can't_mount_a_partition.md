---
title: "I can't mount a partition"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by pabloiran on 2006-11-14
Hi, excuse me for my English (I'm Spanish).

I have two discs, in the first disk I have a windows partition, the swap partition and a reiserfs partition. This reiserfs partition I use it as a "box".

In the other disc I have the Ubuntu partition. This is the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=bebec0d2-af6c-47fd-9789-76769f43e6e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
#UUID=edae82cb-f43d-45bd-92ef-0a68d89d39b6 /media/homesuse ext3    defaults        0       2
# /dev/sda2
UUID=e7067159-fe9b-40ca-af0f-c662f4056861 /media/magatzem reiserfs defaults        0       2
# /dev/sdb2
#UUID=5e2853b5-df92-465b-9f3d-f29921f39628 /media/suse     ext3    defaults        0       2
# /dev/sda1
UUID=9E14CEC814CEA29F /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=e775eda4-488d-4f70-9516-a3664d80b96d none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Well, my problem is that I can't write as a normal user in /media/magatzem (the reiserfs partition). I have written other options but the result is the same, I can't write there as a normal user (but yes as a root). Which options are correctly?


Thanks

---

