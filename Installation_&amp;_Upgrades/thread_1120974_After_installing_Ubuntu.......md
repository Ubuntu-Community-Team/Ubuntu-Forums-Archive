---
title: "After installing Ubuntu......"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-09
The directories that I specified to different partitions; after installation will these partitions be available in 'Computer' (In gnome, KDE etc...)...or can they be only accessed as /[directory]?

Further more will you need root privileges to write on them?

---

### Post by taurus on 2009-04-09
If you want to access other partitions after install, you can add entries in /etc/fstab to have them mount automatically each time you boot Ubuntu.  What filesystems are those partitions?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by dE_logics on 2009-04-10
resierFS, JFS or XFS

You mean those assigned partitions right?

---

### Post by dE_logics on 2009-04-10
Can somone pls confirm this?

---

### Post by dE_logics on 2009-04-11
I need the answers ppl.

---

