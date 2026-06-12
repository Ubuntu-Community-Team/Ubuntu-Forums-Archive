---
title: "Partition"
date: 2009-12-22
forum: Hardware
---

### Post by Nameo0 on 2009-12-22
Hi, I installed Ubuntu and I also have Windows Vista.

1) I was wondering how you can change the partition size after Ubuntu has been installled.

2)Is it possible to get rid of Vista completely if you do not want it/ do not neeed it anymore?

---

### Post by IcarusR on 2009-12-22
You can boot from 'live CD' & use Gparted to resize partitions.

Aplicatios > Accessories > Terminal & type 

```
sudo gparted
```

If you no longer want/need windows yes you can 'get rid of it'.

Use Gparted to delete windows partition, then increase size of Ubuntu partition.

---

