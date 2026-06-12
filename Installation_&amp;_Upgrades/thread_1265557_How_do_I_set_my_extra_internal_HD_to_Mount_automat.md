---
title: "How do I set my extra internal HD to Mount automatically?"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by hitekwaiter on 2009-09-13
I've been playing around with Linux for about 2 years, and decided to really get into it. I have purchased a new system w/Intel Core Duo processor and very fast ram. The case is huge and has room for about 10 drives. 

I only have 2 Sata drives installed, other than the boot drive. They mount fine, but I have to do it manually each time going to 
Places -> Removable Media.

So, samba shares that I create on these two drives (which I obviously use to share data with other computers) go away everytime I reboot and remount them.

Using the mount utility, what can I do so these two drive always mount automatically on boot up? My USB drive has no problem.
Also, they are both ext3 and I don't have a dual boot system.

Thanks in advance for your advice

---

### Post by StuartN on 2009-09-13
First type "blkid" to find the UUID of each partition that you want to mount. Then edit the /etc/fstab file, adding one new line for each of your new partitions following the guide in the comments at the top of the file and the existing entries.

---

### Post by hitekwaiter on 2009-09-15
> **StuartN said:**
> First type "blkid" to find the UUID of each partition that you want to mount. Then edit the /etc/fstab file, adding one new line for each of your new partitions following the guide in the comments at the top of the file and the existing entries.


Sorry, but I did this as root. 
here is the FSTAB FILE:
UUID=10ebf996-a44e-4159-a246-732ca62e57e9 / ext3 defaults 0 1
UUID=9690ca33-51d6-44a8-8805-1fd623071094 swap swap sw 0 0
UUID=15c2adb7-2c76-4616-8134-d921953af47f / ext3 defaults 0 1

I DOUBLE CHECKED THE UUID. what did i do wrong??

---

### Post by Whiffle on 2009-09-15
is that the whole FSTAB?  

It looks to me like the first and third ones have the same mount point ( / ), they should have different mount points.

---

### Post by hitekwaiter on 2009-09-16
okay, point me to instructions on how to set the mount points in fstab. I've looked several places. 
oh..and thanks that does help

---

### Post by Whiffle on 2009-09-16
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda1       /backup         ext3    defaults        0       2

```

From left to right:
-the device, in your case this would be: UUID=15c2adb7-2c76-4616-8134-d921953af47f
-the mount point, which is a directory in the root filesystem, such as /mnt/drive  This directory needs to be created before you try to mount the drive
-type: the type of file system, ext3
-mounting options:  the options/permissions the drive should be mounted with, such as noauto, defaults, etc.  ( "man fstab" will have more information about this)
-dump/pass, I forget what these are but I usually set them to 0 0

---

