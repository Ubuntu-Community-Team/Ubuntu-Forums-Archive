---
title: "Invalid partition table on USB flash drive"
date: 2012-11-15
forum: Hardware
---

### Post by 25tom on 2012-11-15
Trying to format a USB flash drive, using gparted, to FAT32, in order to install a Debian Live system (which is a hybrid iso file) using the dd command. Once I've used the dd command, I get an error saying "Invalid partition table - recursive partition on /dev/sdb" in gparted. I've tried making a new partition table, but that also failed. What can I do?

Thanks in advance for any help :)

---

### Post by 25tom on 2012-12-15
Someone I know wiped the disk using Windows. This solved the problem. I was then able to use Unetbootin to write the OS to the drive (though it took a couple of tries).

---

### Post by djschwartz on 2013-01-23
I'm stuck on this too, but I don't understand your solution.  What does "wiped the disk" mean exactly?  Did you format it to fat?  Was that before of after using dd to install Debian on the USB drive?  Did you still do the gparted step?

---

### Post by Joao Lacerda on 2013-01-23
Hi friend!

That is what I do,

GParted
Unmount the disk
Delete the partition
make a new one 
format it using what do you want it to be.

and that is all.

Good luck

All the best

---

### Post by tgalati4 on 2013-01-23
I don't think it is that simple.  USB and SD flash disks use a different cylinders, heads, sectors count scheme than normal hard disks.  You need to find an identical, working USB flash drive and determine the CHS count.  Then use a command line tool to format it with the correct CHS count.  Works the same with SD cards, although it's easier to put it in a digital camera and format it with the camera.  Windows may format a USB stick correctly.

As a general rule:  Don't use gparted or parted or fdisk to format SD cards and USB thumb drives.  They will mess them up.  It is correctable, but you have to find the correct CHS count from an identical drive.

---

