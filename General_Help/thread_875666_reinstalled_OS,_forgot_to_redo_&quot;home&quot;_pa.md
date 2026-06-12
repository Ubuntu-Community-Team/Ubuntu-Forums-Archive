---
title: "reinstalled OS, forgot to redo &quot;/home&quot; partition properly. help needed"
date: 2008-07-31
forum: General Help
---

### Post by modulistic_terror on 2008-07-31
I decided to remove 32 bit hardy and install 64 bit in its stead, at which point I totally forgot to set my home partition to /home and now it is just a mountable partition in the places menu. After i installed all updates etc I installed gparted and I am unfortunately unable to set things right. If anybody could help me figure out how to do this ill be forever grateful. Thanks in advance.

---

### Post by Vishal Agarwal on 2008-07-31
install the package webmin.
it is a nice package giving so many facility, regarding system. in that package you will find hardware -> Partitions on Local Disks. there you can define your partition and solve your problem. Also it has System -> Disk and Network Filesystems, there u can mount different folders and partitions.

be sure to take a backup before proceeding, so that if u found some error u can restore it. 

Playing with disk partitioning is very dangerous, be careful.

---

### Post by plucky on 2008-07-31
> **modulistic_terror said:**
> I decided to remove 32 bit hardy and install 64 bit in its stead, at which point I totally forgot to set my home partition to /home and now it is just a mountable partition in the places menu. After i installed all updates etc I installed gparted and I am unfortunately unable to set things right. If anybody could help me figure out how to do this ill be forever grateful. Thanks in advance.

See the Psychocats tutorial for [seperate home partition](http://www.psychocats.net/ubuntu/separatehome)

Good Luck

---

### Post by zvacet on 2008-07-31
```
sudo cp /etc/fstab /etc/fstab.bak
```

```
gksudo gedit /etc/fstab
```

Your partition is probably named something like this
/media/hda2           ext3    relatime        0       2


Rename it to 

/home       ext3    relatime        0       2

I hope this will help.

---

