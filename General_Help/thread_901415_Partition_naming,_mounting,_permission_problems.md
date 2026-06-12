---
title: "Partition naming, mounting, permission problems"
date: 2008-08-26
forum: General Help
---

### Post by vern3219 on 2008-08-26
I have Ubuntu 8.04 OS installed on my computer. When I click on “places” then “home folder” the display shows on the left side the partitions that are mounted. The problem is that all of the partitions are named as xx.x GB media with no way of knowing which one is which! What happened to the naming  of partitions as /dev/sdx.y? When I right click on a partition it is possible to open, open new window or umount, the remove and rename options are grayed out. After moving the partitions to the desktop I right click on one of them and then click on “properties” and then am able to see that the partition name as /media/disk-X. This is a long way to go to find out which partition it is. Is there a way to rename a partition to the old standby /dev/sdx.y?

When looking at /etc/fstab the only partitions that are listed are “/”  and “swap”. How do all the other partitions get mounted because all the unlisted partitions have been mount on startup?

There are three ways to name each partition /dev/sdXY, /media/disk-X and UUID. Way are there three ways to name each partition?

With these three ways of naming each partition there are three different sets of permissions for each! That makes it difficult to determine which set of permissions is to be used? Is there a way to get all three to the same set of partition?

I have been unable to find any man pages, howtos and such on /media and UUID. Is there any help info on these items?

Why all this is because I want to be able to control my partitions and know what is happening! I have followed Linux from the start. When distros became availabe I try a number with RedHat release I started dual booting with Microsoft. It used to be easy to work with partitions but with the last couple of releases it is just getting too complicated and know I am starting to think of MS since it does not make using partition a confusing mess!

Thank you
Clayton Stapleton

---

### Post by raphaelr on 2008-08-27
Hmm first the Documentation problem... There should be man pages for **mount**, **umount** and **fstab**.
Next the automaticly mountet patrions. I'm not sure but I think Ubuntu is running a daemon checking for new drives. It's only a guess.
Next you need to be root to change the entries in /media. Thus rename is greyed out.
Finally for the bad name problem. You can try following. First unmount everything. CD into /media and use sudo 'umount sda1' etc. Next change the name of the entries. It's actually better to use symlinks so 'sudo ln -s YourNewDriveName sda1'. Then add all drives you have to /etc/fstab. As target folder choose either '/media/sda1' or '/media/YourNewDriveName'. Now you can use 'sudo mount -a' to mount everything in your fstab.

Hope that helps.

---

### Post by jerome1232 on 2008-08-27
Just to add I've noticed that the automount thing will name them by volume label if it's available.

When I format partitions using gparted I give my usb disk the label 'backup' When I plug it into any Ubuntu machine it gets mounted as /media/backup.

If there's no volume label it just mounts them as /media/disk, /media/disk-1, /media/disk-2, in order of discovery and labels them by volume size.

---

