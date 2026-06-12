---
title: "Having trouble recovering data from disk img"
date: 2011-01-19
forum: Hardware
---

### Post by hyjalsoul on 2011-01-19
I have 2 RAID1 hard drives with possibly hardware errors, (when I tried to mount them in a degraded array, they won't start, throwing some Buffer I/O errors) 
So I used ddrescue to make a disk image out of one drive, ran losetup to use the image file as loopback device:
```
losetup /dev/loop0 imagefile.img
```
but when I tried to assemble a raid array including the /dev/loop0 device like:
```
mdadm --assemble /dev/md0 --force /dev/loop0
```
it will complain that no superblock is found on /dev/loop0 device.

With desperation, I tried to create a legacy raid array with following command, of course, including one of the bad drives:
```
mdadm -B /dev/md0 --level=1 -n2 /dev/sdb1(bootable partition on the bad drive) /dev/loop0 
```
I successfully created a new RAID1 array, but when I tried to mount it 
```
mount /dev/md0 /mnt/tmp
```
it failed because of bad drive sdb
and after I stopped raid array, the disk image file got contaminated too, because I don't see something like anymore:
```
   Device Boot      Start         End      Blocks   Id  System
         /dev/loop0p1   *           1       29664   238267392   83  Linux raid autodetect
         /dev/loop0p2           29664       30402     5928961    5  Linux raid autodetect

``` 

it only left me one partition with ext4 system on it 

Now the only thing I haven't tried is to clean the superblock by doing --zero-superblock, and not sure if that will solve the problem.

Should I get a second drive to hold my broken drive image so that I might be able to assemble a good RAID1 array or should I continue working on the only disk image file I recovered from one of the broken drives?

---

