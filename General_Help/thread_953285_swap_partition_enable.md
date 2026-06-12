---
title: "swap partition enable"
date: 2008-10-20
forum: General Help
---

### Post by namaster on 2008-10-20
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=24f320fa-a237-4daa-89f2-cab7048096d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2ad03d11-86cc-43ef-ba22-7102787c4fa3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Does this means my swap partition is working?

---

### Post by p_quarles on 2008-10-20
Not necessarily. Try running:
```
free -m
```
and post the output here. That will tell us for sure. The contents of /etc/fstab only tell you if it's configured, not if it's acutally working.

---

### Post by namaster on 2008-10-21
> **p_quarles said:**
> Not necessarily. Try running:
```
free -m
```
and post the output here. That will tell us for sure. The contents of /etc/fstab only tell you if it's configured, not if it's acutally working.

```

            total       used       free     shared    buffers     cached
Mem:          2025       1651        374          0         48        890
-/+ buffers/cache:        712       1313
Swap:         2055        232       1822


```

I guess its working. But why it doesn't show anything in shared, buffers and in cached? Thanks for the help.

---

