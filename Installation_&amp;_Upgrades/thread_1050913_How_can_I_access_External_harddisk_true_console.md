---
title: "How can I access External harddisk true console ?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-01-26
I have an external harddisk that I can see "Name:41,2 GB Media", I have some files that I want to run how do I get to it in the console ?

---

### Post by Tim Sharitt on 2009-01-26
If you have already mounted it in nautilus, it will likely be mounted at /media/disk (or if other disks are already mounted disk-1, disk-2, and so forth).

If it is not already mounted, you will need to mount it to an empty directory.
```
sudo mount -t [file system type] /dev/sdxy [mount point]
```
You will need to substitute the proper file system, block device, and mount point.

For example, if you only have one internal drive and an external drive with a fat32 file system which you wish to mount at /mnt/disk, you would do the following:
```
sudo mount -t vfat /dev/sdb1 /mnt/disk
```
If you are not sure of your disk block device, run
```
sudo fdisk -l
```
to bring up a list of available partitions.

---

