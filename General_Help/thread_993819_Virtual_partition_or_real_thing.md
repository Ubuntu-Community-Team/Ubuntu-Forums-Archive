---
title: "Virtual partition or real thing?"
date: 2008-11-26
forum: General Help
---

### Post by hoze on 2008-11-26
i wanned to free some disk space when i noticed that i have the wubi in my d:\ ntfs partition (d:\ubuntu), it takes 13GB.
i booted the ubuntu and i started Gparted, i wanned to resize the D:\ partition,
but i cant resize any partition, does that mean that the ubuntu is installed on a virtual partition inside the windows?
my ext3 partition is 15GB, 3.85GB used,
but... 13GB in D:\ubuntu and the 15GB ext3 is too much for 80GB hard drive.
also i installed Norton PartitionMagic, it shows the ext3 and the swap partitions (ext3 is shown as full, 0b free).

question: how can i check if my ubuntu is not installed on a virtual partition?
if is or not, is it safe to delete the d:\ubuntu?
will i lose my ubuntu if i delete d:\ubuntu?

thank you.

---

### Post by hoze on 2008-11-26
nobody even wants to look? 
can any1 help please?

---

### Post by hoze on 2008-11-27
anyone?

---

### Post by Elfy on 2008-11-27
Bumping a thread after an hour probably didn't help - people look for 0 replies :)

If you installed ubuntu with wubi then it is in fact a virtual partition - D:\ubuntu will be the whole of your system and deleting it will do just that.

It can be resized but you need to use lvpm - [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

---

### Post by hoze on 2008-11-27
thank you

---

