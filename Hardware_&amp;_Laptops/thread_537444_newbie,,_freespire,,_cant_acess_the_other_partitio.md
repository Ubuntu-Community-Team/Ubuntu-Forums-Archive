---
title: "newbie,, freespire,, cant acess the other partitions"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by be_direct2002 on 2007-08-28
i am new to linux,, i cant seem to get anywhere on the freespire forums,, can someone help me figure out how to access the other partitions on my 2 hard drives they tell me i dont have permission..

---

### Post by merlinus on 2007-08-28
Post output of:

```

sudo fdisk -l
cat /etc/fstab

```

-merlin

---

