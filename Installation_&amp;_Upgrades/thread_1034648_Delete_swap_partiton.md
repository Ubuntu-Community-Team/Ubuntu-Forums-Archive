---
title: "Delete swap partiton"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by _TUX_ on 2009-01-08
Hey, I triple booted Vista, XP, and Ubuntu 8.10 and Ubuntu can see the other partitions but xp and vista cant see the Ubuntu partition. I already tried the ifs driver but it didn't work so i decided to make a shared partition but I already reached the maximum of 4 partitions. So i wanted to ask if it is safe to delete the swap partition? I don't use hibernation, just suspend.

---

### Post by cdtech on 2009-01-08
It's safe to delete, although the kernel is still implementing the swap within the code so it's always good to have some swap space. You can just use a swap file rather than a partition.

---

### Post by Tim Sharitt on 2009-01-08
If you have plenty of physical memory, it should be safe to delete it. However, with no swap, when you run out of physical memory you could run into problems.

---

### Post by _TUX_ on 2009-01-08
uummm... How do you make a swap file and not a partition?

---

### Post by logos34 on 2009-01-08
Yes, you can delete it (I assume you have plenty of ram, like >1 GB).  Just make sure to comment the line in /etc/fstab so linux doesn't try to mount it again

Better yet, why don't you delete it, then create an **extended** partition, then create a new one on a **logical** partition inside, along with the others?  You can make practically as many logical partitions inside as you want. (up to 63)

---

### Post by _TUX_ on 2009-01-08
Yes i have 2GB of ram, how do you make a logical partition?

---

### Post by logos34 on 2009-01-08
use gparted in ubuntu

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
(->'creating a new partition')

---

### Post by cdtech on 2009-01-09
> **_TUX_ said:**
> uummm... How do you make a swap file and not a partition?

The advantage of a swap file is that you don't need to find an empty partition or repartition a disk to add additional swap space. If your still interested, here is how to create a 1GB file, type:
```
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```
/swapfile is the name of the swap file, and the count of 1048576 is the size in kilobytes (i.e. 1GB). Similarly, mount it using the swapon command:
```
swapon /swapfile
```
The /etc/fstab entry for a swap file would look like this:
```
/swapfile       none    swap    sw      0       0
```

Hope this helps.......

---

