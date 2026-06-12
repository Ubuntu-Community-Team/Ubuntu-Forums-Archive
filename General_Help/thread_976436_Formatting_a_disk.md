---
title: "Formatting a disk"
date: 2008-11-09
forum: General Help
---

### Post by Syg on 2008-11-09
I have a second hard drive I want to format, except I don't know where to start. (I would love a good ol' fashioned, Windows/DOS style "format d:".) What commands do I use, and which filesystem should I format to (is ext3 pretty much the standard for Ubuntu)?

---

### Post by taurus on 2008-11-09
Install gparted (if you don't already have it on your system) and use it to format your new harddrive as ext3 then.

```
sudo apt-get update
sudo apt-get install gparted
```
It should now be in System -> Administration.

---

### Post by dburnett77 on 2008-11-09
The command line options are:

parted -- which will set up the partitions

mkfs -- formats the partitions with the desired file system

gparted is a lot easier to use, and creates the file systems.  Also, parted can format.

---

### Post by Syg on 2008-11-09
Gparted looks like the way to go, thanks.

---

