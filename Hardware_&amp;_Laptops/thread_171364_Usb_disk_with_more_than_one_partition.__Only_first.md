---
title: "Usb disk with more than one partition.  Only first persion gets correct permissions"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by drgilberto on 2006-05-06
I have a supertalen usb disk.  I use the gnome desktop.  When I insert the usb drive in my computer, it gets recognized and it mounts the drive.  I get correct permissions, as I am in the plugdev group.  So far so good.

My usb disk had one fat16 partition.  I decided to creat 2 partitions, the first as fat16 and the second as ext3.  That was easy with gparted.  So far so good.

When I insert the drive, both partitions get correctly mounted.

**The problem: Only the first partition gets the correct permissions.  The second partition is owned by root.**

I found some threads but none of the solutions helped.

**How can I tell my Ubuntu Dapper that I want that all partitions on the USB drive are read and write permitted for the plugdev user/group.**

Thanks for helping out.

---

### Post by Sutekh on 2006-05-07
I'm not sure how to change any settings so that the gnome-volume-manager (does the automounting) will set the correct modes of access on all the partitions.

Thankfully you formatted the second partition with a Linux filesystem, so you are free to use **chown**, **chmod** to change the owner of the partition, and the mdoes of access.


This command uses **chown** to change the ownership of the partition to **user** and the group ownership to **plugdev**.  
```
sudo chown -R **user:plugdev** /dev/sda2
```
Of course you can change these to the owner/group owner you wish to use.  I don't know what node the partition exists at, so I am using /dev/sda2 as an exmaple.  The **-R** option makes the command recursive through all sub-folders in the partition.


This command uses **chmod** to change the modes of access (permissions) of the partition.  Use this [CHMOD calculator](http://www.onlineconversion.com/html_chmod_calculator.htm) to help you decide what modes of access you want to use.  I have chosen **777** which allows read/write/execute access for the owner/group owner and everyone else.
```
sudo chmod -R **777** /dev/sda2
```

---

