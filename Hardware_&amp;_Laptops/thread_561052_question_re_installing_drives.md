---
title: "question re installing drives"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by FrankVdb on 2007-09-27
I have a couple of questions regarding two drives I added to a Ubuntu PC (it's actually a Linux Mint install).

I installed the root system on the SATA drive that came with the PC. After that, I added one IDE drive and one SATA. After partitioning, Ubuntu sees both drives. No problems up to that point.

Now, in Nautilus the drives are indicated by the space they have on offer, no drive names are mentioned. When I try to open the drives by doubleclicking them, the first thing the system is asking, is my password... After giving my password, the disk names change into "disk" and "disk-1" respectively. The problem, however, is that nothing can be copied to the drives, so I'm a bit puzzled.

This happens on both drives. Anyone who knows what's going on? I guess I missed something important...

What's causing the permission problem? Do I have to edit fstab? Is there a general howto for fstab? 


My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=40e67eee-0445-42a1-a4bb-eba40d45ba3d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0adbfb62-1b59-4661-b503-ff9462b1e4a8 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

The drives I added are clearly not in there, they are /dev/hdb (=IDE) and /dev/sdb (=SATA) respectively. 

Any help is kindly appreciated. 

Kind regards from Belgium,
Frank

---

### Post by leonidas666 on 2007-09-29
> **FrankVdb said:**
> 
What's causing the permission problem? Do I have to edit fstab? Is there a general howto for fstab? 
Normal users are only allowed to mount disks if they are in fstab. That's why ubuntu is asking you for the password when you want to mount the disks, because they are _not_ in the fstab. However, even if the disk is mounted as root, the users should be able to write to the disk. That is, if the disk is ext3 and the directory where you want to write to is set to allow write from the user. If it is a fat/ntfs disk, then the whole disk is owned by root (unless you told mount to change the permission, but this is a bit complicated), not allowing changes from the users.  
I'm no fstab expert, when i make changes i just look at the other entries and copy the relevant parts. I don't know of a gerneral fstab-Howto, but you could start looking for more info here:
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)
or just type
> man fstab
in the console.

---

