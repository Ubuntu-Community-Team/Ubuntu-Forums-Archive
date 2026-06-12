---
title: "Error on upgrading"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by astrobalaji on 2009-07-16
hii,

When i upgrade my ubuntu it says there is no enough disk space. 
Is there a possibility of increasing the memory of ubuntu. as i have only selected 5gb for ubuntu.

---

### Post by Partyboi2 on 2009-07-17
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
df -h
```
this will show us disk space usage.

---

### Post by tommcd on 2009-07-17
It is not the "memory" that you need to increase. You need to increase the hard drive space that you have allocated for Ubuntu.

Open a terminal (applications > accessories > terminal) and post the output of:
```
df -h
```
and
```
sudo fdisk -l
```
A default install of Ubuntu takes up about 3GB. If you only allocated 5GB for Ubuntu, then the partition tool may have allocated less than 5GB in order to make the partition end on a cylinder boundary.

To increase the size of your Ubuntu partition, get a Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
Boot from the Parted Magic live CD and see if you can increase the size of your Ubuntu partition. This will require you to take space from a contiguous partition on the hard drive, if you can. This will avoid having to reinstall Ubuntu.

The other option is to reinstall Ubuntu. Choose manual partitioning. Then delete your current Ubuntu partition. Then create a new ext3 partition for Ubuntu of at least 10GB if you can. Also create a 1GB swap partition. Then install Ubuntu as you did before.

And welcome to the Ubuntu forums!

---

### Post by astrobalaji on 2009-08-07
thanks a lot...

---

