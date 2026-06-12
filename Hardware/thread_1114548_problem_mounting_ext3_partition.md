---
title: "problem mounting ext3 partition"
date: 2009-04-02
forum: Hardware
---

### Post by drewm1732 on 2009-04-02
Hey everyone, I'm trying to mount a partition i created named sda3 which has a ext3 file system and I'm using Ubuntu 8.04. I'm an undergrad computer science major and have been using an Ubuntu system for a while but I realized that I don't really know much about the way a linux system works. Thats when I stumbled upon a site, and a book, called linux from scratch that guides you through building a lightweight linux system. I obviously got through partitioning the drive but when it comes to mounting the instructions say the commands are

create a mount point and assign it the LSF variable:

export LFS=/mnt/lfs

create the mount point and mount the LFS file system:

mkdir -pv $LFS
mount -v -t ext3 /dev/sda3 $LFS

when i run the mkdir command it says there is a missing operand, does anyone know how the code should really be implemented?

---

### Post by dmitriyp13 on 2009-04-02
What is the exact error message?

---

### Post by drewm1732 on 2009-04-02
it says mkdir: missing opperand

---

### Post by dmitriyp13 on 2009-04-03
It should be created.  The above syntax is correct but for some reason mkdir thinks that part of the command is missing.

---

