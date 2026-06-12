---
title: "Read/Write issues"
date: 2005-11-13
forum: General Help
---

### Post by Skerit on 2005-11-13
Here I am again with my latest problem ;)

For some reason, and I truly have no clue, some of my hard drives suddenly become read-only drives. I want to delete a file, create a map, paste some files and it tells me I don't have sufficient rights to do so. I look at the rights of the drive and everything is correct, I can't even touch it as root

Only option is to reboot the computer and then it works again. 

Ow yes, I'm starting a lot of threads here lately but only to ask questions to which I can't find the answer, the forums have been very helpful on many occasions without me needing to start a new thread.

---

### Post by nszabolcs on 2005-11-13
post the output of
```
sudo cat /etc/fstab
```
```
df
```

---

### Post by aysiu on 2005-11-13
Are these Windows partitions? What's the output of ```
sudo fdisk -l
```?

---

