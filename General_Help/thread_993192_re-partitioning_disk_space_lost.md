---
title: "re-partitioning disk space lost"
date: 2008-11-25
forum: General Help
---

### Post by directcharitycontribution on 2008-11-25
before creating separate /home 15GB drive had approx 3gb free now after re-partitioning /root has 10.04GB AND /home 2.61gb and 1GB free. surely the original partition, 10.04GB, should be now 7GB with 3GB free. How can the disk space be reclaimed?

---

### Post by CatKiller on 2008-11-25
Did you move the files from your old Home folder, or are they still there, underneath the new /home partition?

---

### Post by directcharitycontribution on 2008-11-25
> **CatKiller said:**
> Did you move the files from your old Home folder, or are they still there, underneath the new /home partition?

did this, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by CatKiller on 2008-11-25
So did you do this step? > If you find that you are running out of room on your old partition and you're pretty confident everything is working as it should be, then go ahead and delete the backup of home:

```
sudo rm -rf /home_backup
```

---

### Post by directcharitycontribution on 2008-11-25
> **CatKiller said:**
> So did you do this step?

yuh. 

i got headache and just want to regrade to 8.0

---

### Post by CatKiller on 2008-11-25
I've looked at your numbers again. Before you re-partitioned, you were using about 12 GB of your hard drive. After you re-partitioned, you're using about 12 GB of your hard drive. Is the discrepancy really that great? How much space you have on each partition is entirely dependent on how large you made each partition. Unless I'm missing something from your description; it's not entirely clear how large each partition is.

---

