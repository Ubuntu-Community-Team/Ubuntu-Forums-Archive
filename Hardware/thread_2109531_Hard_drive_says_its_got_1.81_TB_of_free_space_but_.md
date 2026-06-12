---
title: "Hard drive says its got 1.81 TB of free space but progams in ubuntu says otherwise"
date: 2013-01-27
forum: Hardware
---

### Post by shawnstoebe09 on 2013-01-27
So im I was installing StarCraft 2 and it installed just fine but when it wanted to patch it said im out of disk space but i got 1.81TB left on my hard drive.. Also Ubuntu 12.04 isn't even seeing my 80GB hard drive even though I told Ubuntu to install on that drive. On places it says 2.0TB file system so there must be something I'm missing please help!

---

### Post by papibe on 2013-01-27
Hi shawnstoebe09.

Could you post the result of these commands?
```
mount -l

df -h

df -i

sudo fdisk -l
```
Regards.

---

