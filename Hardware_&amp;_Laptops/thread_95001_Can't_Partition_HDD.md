---
title: "Can't Partition HDD"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by souled on 2005-11-25
For some reason, I can't partition /dev/hdb. When I try to set the disklabel to msdos with parted, I get this error. ```
(parted) mklabel msdos
Error: Input/output error during read on /dev/hdb
Retry/Ignore/Cancel? 
```

Is there something wrong with my hdd? Or is there some kind of disk checking utility I can use to see what's wrong with my hdd?

---

### Post by aysiu on 2005-11-26
Maybe it's mounted? You can't modify a mounted partition with a partition editor.

---

