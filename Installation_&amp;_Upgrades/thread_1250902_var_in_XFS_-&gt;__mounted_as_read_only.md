---
title: "/var in XFS -&gt; / mounted as read only"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by cdubet on 2009-08-27
I have installed a second hard disk and wished to install /var on a new partition on  this disk (XFS partition)

I have booted on ubuntu CD, formated the 2nd hard disk DD and changed the /etc/fstab
Then I have copied (with cp -ax) the contents of my existing /var in the new partition
I have created an empty  /var so ubunu can mount it

When I reboot, / is always mounted as read only :-(
and /var is correctly mounted (ie read wand write ...)
I tried fsck /dev/sda1 -> disk clean

If I cancel my changes (restore the /var in the first hard disk and reboot), everything is OK

Where is the problem ?
Is it in my  fstab or is there a problem with xfs or I have missed something somewhere ?

my /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/sda1    /    ext3    relatime,errors=remount-ro 0       1
#/dev/sdb1    /var    xfs    defaults    0    1

# swap was on /dev/sda5 during installation
UUID=8fce3452-1e4b-4c53-baa8-dea9ba2c8da4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by cdubet on 2009-08-29
I have just changed the /var in /home in fstab as I have used the partition now for my home directory. 

And it works fine ...

I wonder what was wrong with /var 
If anybody has an idea ...

---

