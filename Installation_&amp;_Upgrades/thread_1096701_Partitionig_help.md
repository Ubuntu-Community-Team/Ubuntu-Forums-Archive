---
title: "Partitionig help"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by InF3XioN on 2009-03-15
I have an 160 GB HD divided in two partitions. In the first one I had installed Windows and in the second one, Ubuntu 8.10. I recently decided to merge the two partitions into one, and use only Ubuntu. But there is a problem with gParted. I think it can't merge the two partitions. Please help. I don't know what to do.
P.S.:I have copied the Ubuntu partition into the unallocated space that was created after deleting the Windows one.

[[IMG]http://img261.imageshack.us/img261/263/gparted.th.png[/IMG]](http://img261.imageshack.us/my.php?image=gparted.png)

---

### Post by vanadium on 2009-03-15
With your current layout, it is not possible to (easily and quickly) merge the partitions sda1 and sda6. I would advise you the easy way, which is to backup your personal user data, then reinstall Ubuntu from scratch, having it use the entire drive. The installation program will automatically take care of the needed partitioning.

---

### Post by InF3XioN on 2009-03-15
I have a lot of useful data. I can't think of reinstalling for example, my modem's drivers, it was too hard to find compatible ones. There are installed a lot of plugins that are hard to find. I have been using Ubuntu since September. I prefer not to merge the drivers, if I have to do all that stuff.

Is there any way to backup the whole sda6 partition, in an external drive, then format my HD and paste the backed up partition in the unallocated space, resize it and also create a swap? But in thois case I will face problems with the grub.

---

### Post by vanadium on 2009-03-15
It is possible, but not at all trivial. It depends on your current skills and linux knowledge.

There are other options as well. You can just keep your current partitoning, but reformat the former Windows partition for use as a data partition. This would be a safe and easy change.

You could move your /home over there. That is somewhat more difficult and I do not see an important benefit: your system partition is more than sufficiently large to store both system files and user configuration data.

---

### Post by InF3XioN on 2009-03-15
Thanks for your suggestion. Maybe I do that, if I don't find any other solutions. But I think, I will keep trying to find a way to merge them, for the time being.

---

### Post by InF3XioN on 2009-03-15
OK, a friend of mine told me to do this, this way:

1) Delete the sda1 partition, so it becomes unallocated space.
2) Copy the sda6 into the unallocated space as primary, without resizing it.
3) Also create a swap in the unallocated space.
4) Delete the whole extended partition after unmounting the swap that is in use.
5) Resize the unallocated space, to the whole drive's space, so that the two previous partitions (sda1 and the extended) are merged into one.
6) Move the newly created swap to the right.
7) Resize the copy of sda6 to the biggest size.

Is the above method, possible to be done? Please reply.

---

### Post by vanadium on 2009-03-15
More or less, yes. But I told you it is not trivial.

---

### Post by InF3XioN on 2009-03-15
> **vanadium said:**
> More or less, yes. But I told you it is not trivial.

I've managed to do it. I faced some trouble, because I needed to reinstall grub, and edit the /etc/mtab and /etc/fstab files. It was a bit difficult to find where was the problem. But I did it. Thank you for replying.;)

---

### Post by vanadium on 2009-03-16
Then you can call yourself at least a "moderate Ubuntu expert". Congratulations!

---

