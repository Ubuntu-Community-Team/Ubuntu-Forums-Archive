---
title: "Questions about LVM-management"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Kelrid on 2009-11-01
Hello forum!

I've searched for an answer to my question without success. Maybe I used wrong search syntax or maybe is't not possible to achieve what I'm looking for. This is what I've done and what I'm trying to do:

I installed Ubuntu Server 8.04 LTS to one harddrive (/dev/sda). I divide the disk into one /boot and the rest to one large "Managed by LVM" partition.

I called my vg for volg01. (I know, very creative thinking by my part.)

In volg01 I created several volumes and among them a /home vol.

Later on I added a new harddrive (/dev/sdb) and executed

"*pvcreate /dev/sdb*" followed by

"*vgextend volg01 /dev/sdb*" and

"*lvextend volg01 /dev/volg01/home* -l +(all avaible PE) ". After that,

"*resize2fs /dev/volg01/home*".

Everything worked out very smooth, even though I did all this online. (Never umount)

Now to what I'm trying to achieve:

I would like to remove the first drive,  (/dev/sda) from the volume "/home" making "/home" only to reside on second drive (/dev/sdb/).
I've read a lot of guides and posts but have only found out how to remove an entire disk from a volumegroup and that's not what I want. I want to keep the disk in the group just remove it from this volume (/home). Making /dev/sdb to store all /home data and the rest of the system to /dev/hda.

Further on, is there a way to see which volume occupies which disk? Where the PE goes?

Would be tremendous happy if someone could point/hint me in right direction or present  solution.

/K

---

### Post by Kelrid on 2009-11-01
I've found a way to see which disk is keeping the logical volumes.

By typing

*pvdisplay -m*

I can see where all logical volumes are.

Next up, removing a disk from a logical volume. I'm currently researching the *pvmove* command. Perhaps reducing the filesystem on /home to the size of the /dev/sdb will do.
I know it's close now. Just have to straighten it all out in my head. Get the hang of all the terms.
Yes, if it isn't clear by now, I'm a beginner to LVM. But stubborn to learn, I'll prevail.

---

### Post by Kokopelli on 2009-11-01
Try this:

[http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

---

### Post by Kelrid on 2009-11-01
Hey Kokopelli and thanks for the link. Sadly, it doesn't helped me out, well not directly, but it gave me some ideas how to tackle this from a new point of view.

I'm now focusing on *resize2fs *and particually how I can calculate the right block number to fit my harddrive. I learned that blocksize displayed in vl- pvdisplay don't match the blocks *resize2fs* works with.
Yes go ahead, why make these things easy. :?

Must find the ratio, the golden factor to unlock my dream of a correct sized filesystem on one harddrive. How hard can it be?

The hunt goes on... :mad:

---

### Post by Kokopelli on 2009-11-01
resize2fs /home to be small enough to fit on just sdb

then "sudo lvresize -L -200M /dev/volg01/home" replacing 200M with the appropriate size to shrink the logical volume.  Be very careful not to make it smaller than the filesystem stored on the logical volume itself though. That will totally screw you.

then "sudo pvmove /dev/sda"  (P.S. you are really using the physical disk, not a partition on the disk?)

At this stage you have what you asked for.  All of the logical volume that is "home" resides in the physical volume /dev/sdb.  sda and sdb are still part of the Volume Group volg01.  I am not really sure why you would want this since if one disk fails the logical volume is still corrupt.  It does not matter that all of home is stored on sdb. What matters is that the physical volumes contained on sda and sdb are part of the volume group volg01.

Edit think of it this way

You have physical Volumes that are gruoped together to constitiute a Volume Group.  A Volume Group contains a number of Logical Volumes.  LV's care not one whit about PV's nor are they in any way aware of them.  Similarly PV's only know they are part of a specific Volume Group and have no idea what LVs are stored on them.  All a PV knows is how many extents are in active use.  So the fact that you moved a particular LV to a specific PV really serves no purpose and probably even slows down the system a little bit.

---

### Post by Kelrid on 2009-11-01
Thanks a lot for helping me out.

I've done all of the steps you pointed out except I entered,

*pvmove -n/dev/volg01/home /dev/sda2 /dev/sdb *instead of

[I]pvmove /dev/sda .
[/I]
(Yes, I'm using the disk not a partition. Don't know why but that's the result of doing *pvcreate /dev/sdb. *Doing *fdisk* on this disk results in error and no partition found. Not even a "LVM partion". It looks empty but the storage works.)
The reason for the move is to keep all home data, ftp and users backup files on one disk and the system on an other. My thought is to divide the stress between the disks. Reciving the backups and maintaining the system, occupying one disk-pickup each.

And above all, see if I could do it and it seems like I'm on my way.

Thanks for your input.  This issue is now solved. \\:D/

---

### Post by AnotherDave on 2010-01-15
I know this problem is solved, but there is so little information about LVM I thought I'd add this link:

[http://sunoano.name/ws/public_xhtml/lvm.html](http://sunoano.name/ws/public_xhtml/lvm.html)

and, if you are also using encryption:

[http://sunoano.name/ws/public_xhtml/dm-crypt_luks.html](http://sunoano.name/ws/public_xhtml/dm-crypt_luks.html)

---

