---
title: "Terminal to internal mounted media"
date: 2008-08-22
forum: General Help
---

### Post by Jaded Misanthrope on 2008-08-22
What would the path to mounted internal media (in this case, a Vista partition) in the terminal?

---

### Post by WRDN on 2008-08-22
Partitions/ disks are mounted in the /media folder, so you would need to change directory to the relevant folder in /media:

```
cd /media/[vista_partition]
```

---

### Post by dexter.deepak on 2008-08-22
```
sudo mount
```
to see the mounted partitions. guess your vista drive ...something like sdaX, and there will be a correxponding entry for the mount point.

---

