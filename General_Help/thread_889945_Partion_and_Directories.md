---
title: "Partion and Directories"
date: 2008-08-14
forum: General Help
---

### Post by cnic on 2008-08-14
New to Ubuntu and Linux.  I've created partitions on a had drive (dev/sda3) and now want to make a directory on that partition.  When I mkdir I of course make the directory in my home.  How do you "direct" the mkdir command?  In dos I'd mkdir c:\"new directory name."  Thanks in advance and yes, I'm just now trying to make the change to Linux .

---

### Post by Thingymebob on 2008-08-14
You will first need to mount the partition - Have a read of the relevant parts of your well documented linux system manual by entering in a terminal
```

man mount
man fstab

```
May appear to be speaking a different laguage to you at first, if so post back and I'm sure someone will help.

Once mounted correctly you'll be able to create a dir by entering
```

mkdir /mountpoint/directoryname

```

---

