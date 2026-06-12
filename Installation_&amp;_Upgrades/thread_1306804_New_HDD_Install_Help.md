---
title: "New HDD Install Help"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by newguy2 on 2009-10-30
Hello all.

AS you can see for my first post I am need of some info.  I have an older computer I am wanting to add this on to.  I need to change out my harddrive before I do this and need to know what I need to do prior to this.  I assume I need to format it, but what else?  

Thanks Db

---

### Post by lensman3 on 2009-10-30
Add this disk to the machine.

Boot.  Then from a text window do:

"fdisk -l"  The new disk should be listed.  You need the drive number which will look like "/dev/sdx" where x is a, b, c, etc.  


Since this is a new disk it won't have partions so then run "fdisk /dev/sdx" where x was "discovered" before.  Partition the disk to what you want.  Create the parition table and write it. 

Then run mkfs.ext4 which formats the disk so that Linux can find it.   I would suggest you keep the 4k block size. 

Add the new disk to /etc/fstab. Then mount it.

---

### Post by brownwrap on 2009-10-30
> **lensman3 said:**
> Add this disk to the machine.

Boot.  Then from a text window do:

"fdisk -l"  The new disk should be listed.  You need the drive number which will look like "/dev/sdx" where x is a, b, c, etc.  


Since this is a new disk it won't have partions so then run "fdisk /dev/sdx" where x was "discovered" before.  Partition the disk to what you want.  Create the parition table and write it. 

Then run mkfs.ext4 which formats the disk so that Linux can find it.   I would suggest you keep the 4k block size. 

Here is my output of fdisk:

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System


Add the new disk to /etc/fstab. Then mount it.


Here is my output of parted:



Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

I am ready to create two partitions, but don't know where to statrt and end Them. The first one is obvious, it should start at 1, but where do I end it if I want two equal parttitions? Does it want the size in cyclinders?

---

