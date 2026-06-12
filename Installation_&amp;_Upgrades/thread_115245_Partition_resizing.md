---
title: "Partition resizing"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by ajaym on 2006-01-10
I can find a lot of info on partitioning, but not for the specific scenario I want to perform, namely

I have a test machine running Breezy with a single 120G hard drive which I lazily  left with / occupying most of the drive, rather than setting up separate partitions e.g for /var, /usr etc.

I would like to resize the / filesystem and the underlying partition back down to 60G and then create a new partition into which I could install either another distro or (gak) Windows.

My current understanding is that, with the default ext3 filesystem I can boot up the install disk in rescue mode and then

(a) turn off the journalling for the filesystem
(b) resize the filesystem
(c) re-enable journalling
(d) somehow resize the partition - but I wasn't clear on which tool to use for this - I understood that parted could not resize, and there is 'fips' but which is the best approach.
(e) Then create a new partition to span the now unused 60-odd G of space.

I know I could completely re-install, this being a test system, but I wanted to see if this scenario is doable first, because it would be very handy.

---

### Post by lha on 2006-01-10
You can use [GParted]("http://gparted.sourceforge.net/features.php") from Ubuntu livecd to shrink ext2/3 partitions.

---

### Post by az on 2006-01-10
[QUOTE=ajaym]
I would like to resize the / filesystem and the underlying partition back down to 60G and then create a new partition into which I could install either another distro or (gak) Windows.
.[/QUOTE]
If you want to install windows, you will have to free up some space at the beginning of the drive.  Since you cannot change the starting position of a partition, you will have to shrink it, move it to the free space and delete the first partition.

If you want to install another distro, perhaps their installer can automatically shrink a partition with an existing os on it like ubuntu's installer can do.

By default, if you try to install ubuntu again, it will detect your current install and offer to shrink that partition for you.  You just have to enter the size of the new partition.

[QUOTE=ajaym]
My current understanding is that, with the default ext3 filesystem I can boot up the install disk in rescue mode and then

(a) turn off the journalling for the filesystem
(b) resize the filesystem
(c) re-enable journalling
(d) somehow resize the partition - but I wasn't clear on which tool to use for this - I understood that parted could not resize, and there is 'fips' but which is the best approach.
(e) Then create a new partition to span the now unused 60-odd G of space.
.[/QUOTE]

a,b and c - journaling has nothing to do with it.  You have to unmount the partition.  But if you boot the installer, CTRL-ALT-F2 to the shell and you will not even get to the rescue mode.  Nothing will be mounted.
d -  parted

parted /dev/hda 
# this starts parted, the command line partitioner

print
# this lists your partition table.  You should have two partitions the / and the swap

resize 1
# this will resize partition one.  Enter the new smaller size of yor partition

You will now have free space that any linux installer will see and use to install.

You can create a new partition there if you want with mkpartfs in parted.

---

