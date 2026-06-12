---
title: "Finding lost partition"
date: 2008-09-11
forum: General Help
---

### Post by emanuel.landeholm on 2008-09-11
Hi,

I just messed up a 300 GB filesystem when my computer froze while running gparted from an ubuntu livecd ( :evil: ). However, most of the data is also on another hard disk. The problem is that the other hd has been
repartitioned. I have not overwritten the old partition so I think I ought to be able to rescue it if I could only find the starting and ending cylinders somehow.

Is it possible to scan a hd for partition cylinders? Or is the partition table backed up somewhere?

Pls. advice!

---

### Post by Pro-reason on 2008-09-11
Have you tried the following guide: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)?

---

### Post by caljohnsmith on 2008-09-11
There's a good chance you can use "testdisk" to recover your partition:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition. Also post the output of:
```
sudo fdisk -l
```

---

### Post by emanuel.landeholm on 2008-09-12
Thanks for the hints. I tried testdisk and it found the partition but it seems like it has been overwritten after all.

As it happens I found most of the missing files in lost+found in the messed up filesys. I thought I had looked there but I guess not... :)

Note to self: When growing a partition from a ubuntu livecd, do not attempt to install gentoo on another hd.

---

