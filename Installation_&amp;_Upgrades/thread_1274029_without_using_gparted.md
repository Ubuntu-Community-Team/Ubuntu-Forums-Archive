---
title: "without using gparted"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by manojpawar on 2009-09-24
hi all,

Shoud I can do repartition  of my hard disk by using Ubuntu live cd.without using gparted.

---

### Post by earthpigg on 2009-09-24
```
sudo parted
```

---

### Post by pmlxuser on 2009-09-24
> **earthpigg said:**
> ```
sudo parted
```

have to install it firt though right with
```

$sudo apt-get install gparted

```

---

### Post by rreese6 on 2009-09-24
I had to read your question a few times..
Are you asking if you can just use the LiveCD to repartition your Hardrive?
If you are doing a new installation the answer is yes.
if you want to adjust the partitions or replace some of them. then you can use various tools.
Garted is the easiest to use, with parted and fdisk being others.
you can use the LiveCD to boot then run gparted to manually adjust your partition. 
I hope I understood your question correctly.

---

### Post by doas777 on 2009-09-24
yeah, probably. but why would you want to? if you need cli try fdisk or parted

---

