---
title: "mount ?"
date: 2008-11-08
forum: General Help
---

### Post by rusty_jones on 2008-11-08
```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1193

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    b  W95 FAT32

```

How do I mount a hard drive with these settings?

Rusty

---

### Post by taurus on 2008-11-08
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000  0  0
```
Save it and close gedit editing window.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by rusty_jones on 2008-11-08
Thanks, it worked like a charm.

Rusty

---

