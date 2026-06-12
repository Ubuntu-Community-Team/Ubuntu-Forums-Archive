---
title: "Gpart crash with terabyte format"
date: 2009-01-24
forum: Hardware
---

### Post by bluemarble on 2009-01-24
Hi, 
Recently got myself a western digital terabyte external drive. I tried to format my terabyte HD which seemed to work fine then  Gpart froze up just after the formating finished. I went back into Gpart to check out the drive and when I tried to unmount the terabyte Gpart keeps freezing. It says its scanning drives but never stops and the whole system almost stops.:(

Whats up with Gpart?:frown: How can I reformat the drive?


Related Side point:
I was thinking I could parition the drive one for image backups and the secound for media storage. any thoughts on filesystems? ext3, JFS, XFS?

Cheers

---

### Post by taurus on 2009-01-24
You can always format (or even partition) your harddrive from a terminal.

To partition:
```
sudo cfdisk /dev/sdb
```

To format (ext3):
```
sudo mke2fs -j /dev/sdb1
```

---

