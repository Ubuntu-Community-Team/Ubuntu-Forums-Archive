---
title: "Manual repair of start-up"
date: 2008-08-02
forum: General Help
---

### Post by D.M. on 2008-08-02
When booting Ubunu I get the following:

fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Unable to resolve "UUID=F784f9f7-e59f-4a29-9597-5af86d651a4b
fsck died with exit status 8
manually correct

How do I correct this problam?

(I type "exit" and Ubuntu finishes loading and works fine.  I had another O.S. on ext2 and deleted it which seems to have caused the problem.)

---

### Post by sisco311 on 2008-08-02
type:
```
sudo blkid
```in a terminal to list the uuids of the partitions
replace the uuid of the partition in fstab with the new one.
To edit the file:
```
gksu gedit /etc/fstab
```

---

### Post by spiderbatdad on 2008-08-02
check uuid's in /etc/fstab

---

### Post by drs305 on 2008-08-02
> **sisco311 said:**
> type:
```
sudo blkid
```in a terminal to list the uuids of the partitions
replace the uuid of the partition in fstab with the new one.
To edit the file:
```
gkdu gedit /etc/fstab
```

```
gk***su*** gedit /etc/fstab
```

---

### Post by D.M. on 2008-08-02
> **sisco311 said:**
> type:
```
sudo blkid
```in a terminal to list the uuids of the partitions
replace the uuid of the partition in fstab with the new one.
To edit the file:
```
gksu gedit /etc/fstab
```

Thanks and thanks again.  I spent hours looking for the entry, but never in fstab.  Now I know.

D.M.

---

