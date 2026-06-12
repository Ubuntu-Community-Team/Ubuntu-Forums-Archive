---
title: "Wanting Details on The  Partitioning and Filesystem Setup on a Large USB HDD"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by mavigozler on 2009-09-07
I own a **1 TB external HDD** with USB 2.0 connection.  I have [COLOR="Blue"]**Ubuntu 9.04 on a 2.0 GB USB**[/COLOR] stick right now, which I have barely used.  (Now I am resolved to the use of Ubuntu on a regular basis.)

I want to install Ubuntu on the 1 TB drive with the option of being able to boot from the internal 100 GB "code drive" HDD (has Microsoft Window 6.0.6002, a/k/a Vista Home Premium SP2; another internal 100 GB is the "data drive").

My questions are on partition counts (how many and for what purpose?), partition sizes and filesystem formatting.  I have done reading, but still don't have certain answers.

700 GB of the 1 TB drive is already NTFS-formatted so Windows can read it and it is my "backup" drive (files backed up Genie Backup) and "disk image" (the image of the system drive maintained by Paragon BD).

The other 300 GB (probably too much) of the 1 TB drive was partitioned with GNU Partition Editor and is given to Ubuntu, but is unformatted (no filesystem).

The problem is that the 300 GB is on the BACK END of the drive, and so I probably have to move the 700 GB partition so that it frees the boot sectors.  GParted, I have learned, won't do it or refuses to do it.  So I am getting a partition manager (probably from Paragon) to do partition resizing and data moving at the same time (backups not possible).

Now to the **partitioning **and filesystem formatting of the Ubuntu system.  I show the **partitions **as a list below, each item a partition.  I should show three, maybe four, characteristics within the comments on the partition:

[COLOR="SeaGreen"]<partition>:  size, filesystem type, partition type (primary, extended, logical?), and location on disk (physical sector) in relation to other partitions.[/COLOR]

**/boot**:  should be at sector 1?   Maybe 50 MB at the most??  primary type, filesystem unknown (MSDOS type?)

**/swap**:  I have a 2.0 GB RAM.  My reading suggest that 2 X RAM/memory size is correct when disk size not a problem, thus swap size = 4.0 GB.  But other reading indicates that more than 2.0 GB is purposeless.  Which is correct.  'swap' partitiions have their own 'swap' fsys formatting.  Partition type = primary.  Put it just after the boot partition?

**/** (root):  probably an 8 GB size.  Type = primary.  Fsys type = ext3.  Placed just after the swap.

**/var**:  what size??  Type = extended.  Fsys type = ext3 (?)

**/tmp**:  what size??  Partition type = extended.  Fsys type = ext3 (?)

**/home**: 150-200 GB (big guess).  Partition type = primary.  Fsys type = ext3.

**/usr/local**: size= don't really know, but it was recommended.  Probably whatever is left of the 300 GB.  Partition type = extended.  Fsys type = ext3.

Does this scheme look sensible?

I will also need advise on how to install in the boot loader application so that it requests what OS to boot.  My machine BIOS is already configured to look first for a CD/DVD on the optical drive, then poll all USB connected devices, then the internal HDD.

---

### Post by hal10000 on 2009-09-07
> The problem is that the 300 GB is on the BACK END of the drive, and so I probably have to move the 700 GB partition so that it frees the boot sectors

You don't need to free any boot sectors.
The only sense of having a partition at the first sectors of a harddrive would be a slight increase in performance, but you will not need this unless you want to setup a high performance database system or something like this.

So you probably won't need to move any partitions

Now to your partitioning plan:

I assume you want a Desktop Sytem, with no special database- or other servers that are to be used by many users at the same time or for high performance services, is that right? 

If so,then just make one extended partition from the rest of your disk.

You won't need separate partitions for /boot, /var, /tmp and /usr/local, just let these directories reside in a / (root) of about 20-30 GB size (ext3, logical partition)

A swap partition of 1 -2 times the size of your RAM is appropriate (also Logical partition)

The rest of your harddrive can be your /home partition (ext3, logical).

Of course you could create separate partitions for the directories you mentioned above, but it makes only sense if you want to setup a server machine for special purposes.

e.g., a database server usually needs much /var space and/or swap, a mailserver would also want a large /var, an application server would need a large /usr and/or /usr/local, a webserver probably would need a large /www

But, as i said, you should only do this if you want to run such things, because there is one big disadvantage if you do this: You might determine after a time that this or that partition you created is too big or too small for your needs and thus have to be repartitioned or you have to fiddle around with a /tmp partition that is to small serving large temporary files, such as iso images from your DVD or CD Burner

---

### Post by mavigozler on 2009-09-07
> **hal10000 said:**
> I assume you want a Desktop Sytem, with no special database- or other servers that are to be used by many users at the same time or for high performance services, is that right?

Yes, I will use this system for personal use, no other users.  Will do some web development.


Your information was quite helpful in focusing me on how to decide this installation.  I have all the blanks filled in now.

Thanks.

---

