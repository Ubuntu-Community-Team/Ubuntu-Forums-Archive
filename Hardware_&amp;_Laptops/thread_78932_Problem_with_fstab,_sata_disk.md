---
title: "Problem with fstab, sata disk"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by skatedawe on 2005-10-19
My Sata drive doesnt auto mount at startup. It mounts when i type; mount /dev/sda1 /mnt/sata250

 Here's my fstab;

 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hdb1       /home           reiserfs defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda1       /mnt/sata250    reiserfs    defaults,noatime     0       0

```

 Im dont know what the options or type should be. Can somebody plz tell me, im new to this. thx

---

### Post by kairu0 on 2005-10-19
Change "defaults,noatime" to "defaults,noatime,auto".

---

### Post by skatedawe on 2005-10-19
Thank you so much! I think it will work :)

---

### Post by skatedawe on 2005-10-19
It didnt work :(

 Here's the fstab again.

 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hdb1       /home           reiserfs defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda1       /mnt/sata250    reiserfs    defaults,noatime,auto     0       0
```

---

### Post by skatedawe on 2005-10-19
bump

---

