---
title: "Second Drive"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by kennyidaho on 2006-04-10
After a couple tries I finally got Ubuntu installed on a older computer I have. The computer has two drives a 20gig IBM and 40gig WD. I set the 20gig as master and the 40 gig as slave. 

When I boot the machine GRUB claims that I have ubuntu installed on both drives. They way I want it is to have ubuntu installed on the 20gig and then use the 40gig as free space for storage. 

When I installed ubuntu I did a server install because I really want to learn some server side of things and get skilled with the command line. Currently I am using PuTTY to connect to the box.

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I am still fairly new to linux and unsure of a few things. 

I would like to find my second drive and format it for storage use. 

Any help would be great.

---

### Post by taurus on 2006-04-10
Nope.  Ubuntu didn't install on both drives because /etc/fstab doesn't even list your second drive!!!  In your words, you have Ubuntu on the first partition of the first drive, /dev/hda1, while the swap space is on the fifth partition of the first drive, /dev/hda5.  Your second drive is known as /dev/hdb so you first need to create a partition for it.  Then format it and mount it.  Since you already have a terminal, server installed, do
```

sudo fdisk /dev/hdb

```
Now, type n to create a new partition and p for primary.  Then 1 for the first partition.  Then t and type in 83 for Linux filesystem.  Now, you want to write the change and exit with w...  That should drop you back to the prompt again.  Now, format it as ext3; create a mount point for it; and mount it.
```

sudo mke2fs -j /dev/hdb1
sudo mkdir /backup
sudo gedit /etc/fstab
(and add the following line to the end of /etc/fstab...)
/dev/hdb1  /backup  ext3  defaults,umask=0000  0  0
(then save /etc/fstab and exit...)
sudo mount -a
df -h

```
You should now see /dev/hdb1 in /backup...

---

