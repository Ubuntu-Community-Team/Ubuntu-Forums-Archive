---
title: "What is that utility for mounting XP drives?"
date: 2008-12-05
forum: Hardware
---

### Post by fidgaf on 2008-12-05
I had a small utility in Ubuntu that would automatically mount any selected XP hard drive partition on start-up.

I installed a new hard drive and it got confused so I removed it.

Rather stupidly I forgot to note its name and cannot find it again on searching.

Does anyone know what it is called?

Thanks.




ETA: I would consider changing some script or file to auto-mount. What I have found on doing this is quite confusing and often seems to assume that I'm born knowing what Linux/Ubuntu actually calls each of my hard drive partitions and how that related to their XP name. :D

---

### Post by taurus on 2008-12-05
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by fidgaf on 2009-01-28
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

It loads some XP drives but not all. They manually mount just fine after boot.

I'm suspicious that it was a different utility but can't remember.

---

### Post by stchman on 2009-01-28
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Remember ntfs-config is for NTFS drives only.  Some XP drives are FAT32.

---

### Post by fidgaf on 2009-01-28
All my XP drives and partitions are ntfs.

---

