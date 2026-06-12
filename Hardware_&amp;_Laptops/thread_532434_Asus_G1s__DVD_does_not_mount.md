---
title: "Asus G1s:  DVD does not mount"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by jdjacobs on 2007-08-22
I have a new Asus G1s.  When a DVD is inserted, it apparently is not mounted.  No file such as /dev/hda1, /dev/dvd,  or /dev/cdrom is created.  /etc/fstab has the line:

```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I have seen a number of other Asus G1s that appear to have the same problem.  But I have not seen the fix.

Thanks,

---

### Post by marcop13 on 2007-08-24
You have to
sudo modprobe piix

and add piix to /etc/modules

Hope it will work for you

---

