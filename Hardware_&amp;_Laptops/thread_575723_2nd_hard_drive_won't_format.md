---
title: "2nd hard drive won't format"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Paul_G on 2007-10-14
Hi

I have a 250Gb 2nd hard drive on my computer and I seem to be having a few problems with it.

The hard drive kept going read-only on me, and recently whilst doing a fresh install of feisty I tried to reformat the hard drive but gparted keeps failing and fdisk isn't working either.
Whilst running fdisk and mkfs i got the following at the end

Writing inode tables: done
extfs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

I ran fsck on the drive and that came up with
Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1 
(sdb1 is my second hard drive)

then i ran fdisk -l and the drive wasn't showing at all.

I'm slowly running out of ideas, I'm hoping that the drive isn't screwed.

Any help would be great.

---

