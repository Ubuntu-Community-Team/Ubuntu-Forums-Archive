---
title: "USB Drives not Appearing as /dev/sda"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by Rudy246 on 2007-07-30
Hello.

I've spent the last hour or so trying to figure out how to format a USB flash drive, but I keep running into the same problem: when I insert my USB drive, it only appears as /media/usbdisk, but not /dev/sda.

From what I've read, I have to do something along the lines of
```
fdisk /dev/sda
mkfs -t vfat /dev/sda1
```
to format it and make it FAT32 again.

This problem also probably has something to do with my inability to transfer files between my Windows machine and my Ubuntu machine.

I tried doing
```
fdisk /media/usbdisk
```
,but it said it couldn't read it.

I tried to change the permissions of the drive to allow all to read/write/execute, but it wouldn't let me (even after using sudo nautilus). Each time I checked a box, it would automatically uncheck it a second after.

I'm using Ubuntu 6.06 Dapper Drake.
Any help is greatly appreciated, thank you for your time.
-Rudy

---

### Post by likpok on 2007-07-31
When it mounts it to /media/usb, go into a terminal and type
mount

What should result should be a list of various devices and where they are mounted. Find the one that should be in the form of whatever on /media/usb. Whatever, in that case, will be the device for the usb stick

Then do the following to format it as vfat
umount /dev/whatever
fdisk /dev/whatever
mkfs -t vfat /dev/whateverX

---

### Post by Rudy246 on 2007-07-31
Thanks for that, but I get sort of stuck after typing fdisk.

Here's what I put in the terminal:
```
rudy@rudy-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw)
/dev/sdb1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
rudy@rudy-laptop:~$ umount /dev/sdb1
umount: /dev/sdb1 is not in the fstab (and you are not root)
rudy@rudy-laptop:~$ sudo umount /dev/sdb1
Password:
rudy@rudy-laptop:~$ sudo fdisk /dev/sdb1

Command (m for help): mkfs -t vfat /dev/sdb1
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help):

```

I assumed that when it said, "Command," I should put the mkfs -t vfat /dev/sdb1. Any ideas what I did wrong?

Also, you said to type
```
mkfs -t vfat /dev/whateverX
```
What does the X mean? Should I change it from /dev/sdb1 to /dev/sdb2?

-Rudy

---

