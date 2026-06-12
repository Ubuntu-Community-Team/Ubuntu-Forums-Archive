---
title: "Find Hardrive size in Terminal"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by Christ_Guard on 2007-06-22
What do I need to do to see how big a hardrive is from the terminal?

Thanks!

-Christian

---

### Post by yabbadabbadont on 2007-06-22
To see the size of mounted partitions, run ```
df -h
``` To see the total size of the drive, run ```
sudo fdisk -l
```

---

### Post by Christ_Guard on 2007-06-22
Thanks!

---

