---
title: "Problem resizing Ext3 volume on raid5 array"
date: 2008-07-14
forum: General Help
---

### Post by gnicolao on 2008-07-14
I have a Adaptec 3805 controller which had 3 x 750gb drives. I created a Raid5 set, and created a ext3 filesystem on it. I then migrated my data onto the filesystem (decommissioning a NAS with 2 x 750 drives in it). 

Latter I added the other two drives to the controller and via the Adaptec Storage manager grew the volume to span all 5 750gb drives.

Now when I try to resize the ext3 filesystem I using gparted I get the following error:

A Partition cannot have length of -1 sectors
 
So I try and used parted and get the following.

(parted) print all
Disk /dev/sda: 2199GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1499GB  1499GB  primary  ext3         boot 
(parted) resize 1 32.3kb 2199gb                                           
Error: File system has an incompatible feature enabled.   


Some help please.

---

