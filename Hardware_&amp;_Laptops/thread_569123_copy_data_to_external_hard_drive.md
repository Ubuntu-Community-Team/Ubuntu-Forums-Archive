---
title: "copy data to external hard drive"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by rickshawalla on 2007-10-06
I run Ubuntu on an Asus F3M laptop, also partitioned with Vista. When I try to copy files from my data partition to my extrenal HD I get a message saying "You do not have permission to do this". However, there's no such issue in Vista - it copies fine. What do I need to do?

---

### Post by taurus on 2007-10-06
You need to be root to copy files to your external harddrive.  By the way, what filesystem is that external harddrive--ntfs or fat32?

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

