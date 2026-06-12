---
title: "external IDE HDD via adapter not seen by sys? what to do?"
date: 2008-09-07
forum: Hardware
---

### Post by jarbo on 2008-09-07
I have to save data from several HDDs on the IDE-standard used in a xp-machine and therfore formatted in NTFS or FAT, but Ubuntu-System simply does not see them! I used an adapter that allows to switch the HDDs or on USB 2.0 or on the SATA, but none of these connections seems to matter for the sys. What to do? I am using UBUNTU 8.04 as a USER not a superuser. Any ideas?
thanks

---

### Post by sisco311 on 2008-09-07
open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
sudo fdisk -l
``````
sudo blkid
``````
cat /etc/fstab
```and
```
mount
```

---

### Post by jarbo on 2008-09-07
> **sisco311 said:**
> open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
sudo fdisk -l
``````
sudo blkid
``````
cat /etc/fstab
```and
```
mount
```

I will do so....thanks a lot so far, anyhow if it doesnt work, I will come back :-)

---

