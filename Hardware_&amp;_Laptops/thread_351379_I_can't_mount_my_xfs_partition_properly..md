---
title: "I can't mount my xfs partition properly."
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by gnuwtey on 2007-02-01
The details:

My hard disk is 80 GB and has 3 partitions: one for the root system (10 GB, /dev/hda1) a swap partition (1.4 GB, /dev/hda5), and a space for other files (62.53 GB, /dev/hda2). I'm currently trying to get the "other files" partition to mount. I don't want to use ext2 or ext3 because the partition tables take up too much space (1 GB, to be actual.) so I formatted it using XFS, in the hopes of it being exactly 62.50 GB. I formatted it alright, but now I can't mount it.

I'm trying to mount it under /media/files. When I used the terminal to do that, it was accessible, but it didn't show up anywhere else, and the disks manager showed it to be still under the ext3 filesystem.

I'm currently running Dapper Drake. Would upgrading to Edgy Eft help any?

To the mods: if this is in the wrong forum category, could you please move it to the right one? I'm a green user of this forum, and I don't know where half the stuff is.

---

### Post by kerry_s on 2007-02-01
Can you post your /etc/fstab?
gedit /etc/fstab
or
cat /etc/fstab

You probably just need to change where it says ext3 to xfs or auto
(sudo gedit /etc/fstab) to edit

---

### Post by gnuwtey on 2007-02-02
I'll try that... if it doesn't work I'll post again.

OK, it works, but how do I change the owner to myself? I tried using chown, but it didn't work.

---

### Post by kerry_s on 2007-02-02
> **gnuwtey said:**
> I'll try that... if it doesn't work I'll post again.

OK, it works, but how do I change the owner to myself? I tried using chown, but it didn't work.

Try adding ",user" to the fstab line. I don't think you can own the drives though, since it takes root privileges to mount/unmount drives or do you mean you can't read/write? The ",user" lets you read write and mount.

---

