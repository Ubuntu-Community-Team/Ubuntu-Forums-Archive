---
title: "Copy Harddrives using Live CD"
date: 2008-05-21
forum: Hardware
---

### Post by monsieurdozier on 2008-05-21
I there a way to use the Ubuntu Live CD to make an exact copy of a hardrive from one to another.

I have two 10 Gig harddrives, one with an operating system on it, and one just blank.  The operating system one is malfunctioning.  Is there a way to make an exact copy of it to my blank one?

-Monsieurdozier

---

### Post by ASULutzy on 2008-05-21
Yea this shouldn't be too bad... First type```
sudo fdisk -l
``` to get a list of all your hard drives and their partitions. 

Once you figure out which partition is the source and which is the destination (you could just post the output of sudo fdisk -l here and we could help) then I think you could just do```
sudo mkdir /mnt/source
sudo mkdir /mnt/destination
sudo mount /dev/TheSourcePartition /mnt/source
sudo mount /dev/TheDestinationPartition /mnt/destination
sudo cp -ax /mnt/source /mnt/destination
```

edit: you'll probably want to make sure that the partitions are copies of one another, so for that you would want to do```
sfdisk -d /dev/TheSourcePartition | sfdisk /dev/TheDestinationPartition
``` as root. Do this first, before you mount the drives.

---

### Post by mac71 on 2008-05-22
Hi, you could give this a go:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Works a treat for me. You can make a live cd/dvd of your hard drive including all your own data, or make one excluding it- great for passing on to friends.

---

