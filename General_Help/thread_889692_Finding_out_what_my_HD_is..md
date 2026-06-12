---
title: "Finding out what my HD is."
date: 2008-08-14
forum: General Help
---

### Post by OmnificienT on 2008-08-14
I'm trying to determine what my HD is, using DSL (Damn Small Linux that is). I use ls /dev/hd* 

The following is the result:

[[IMG]http://img528.imageshack.us/img528/3496/dslmi0.th.png[/IMG]](http://img528.imageshack.us/my.php?image=dslmi0.png)

A large list of "harddisks". There's only 1 disk, and not more than 4, maybe partitions.

Now how do I find out which one my HD is? I find that I have the same problem with Kubuntu, but there I can easily use the GUI to find out.

---

### Post by az on 2008-08-14
cat /proc/partitions

and

sudo lshw -C disk -short

---

### Post by cariboo on 2008-08-14
The  command you are looking for is:

```
sudo fdisk -l
```

This will list all your hard drives and their partitions.

Jim

---

