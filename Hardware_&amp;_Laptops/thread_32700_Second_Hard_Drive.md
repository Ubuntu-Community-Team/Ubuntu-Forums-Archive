---
title: "Second Hard Drive"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by vassie on 2005-05-09
Hello,
Last night I formatted my PC and installed Ubuntu 5.04, my main drive is 80Gb, however I also have a second 120Gb drive (both IDE).
I moved everything off my 120Gb drive, and wiped it, creating one ext3 partition (/dev/hdb1), I created /media/storage, then added the following to /etc/fstab

```
/dev/hdb1 /media/storage ext3 defaults 0 0
``` 

but, when I boot, it says there is an error on line 05, then when I go into Gnome, the drive isn't mounted

Can anyone help?

Thanks

Ben

---

### Post by defkewl on 2005-05-09
Are you sure that it is /dev/hdb1 and not /dev/hdb ?
CMIIW

---

### Post by vassie on 2005-05-09
[QUOTE=defkewl]Are you sure that it is /dev/hdb1 and not /dev/hdb ?
CMIIW[/QUOTE]
 /dev/hdb is the drive, /dev/hdb1 is the partition

Ben

---

