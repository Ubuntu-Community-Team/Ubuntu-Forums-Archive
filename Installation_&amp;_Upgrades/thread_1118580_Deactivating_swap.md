---
title: "Deactivating swap"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by OskarS on 2009-04-07
Hi everyone!

I recently installed Ubuntu Intrepid on my little Asus Eee PC (I previously had another flavor of Linux on it), but I have a small problem.

During the installation procedure, I selected "Guided Partitioning, use whole disk" instead of manually partitioning it (mostly because I was lazy), but I realized pretty quickly that that included a 600 megabyte swap-partition. Since the Eee PC runs on a solid-state drive, I've come to understand that having swap on that is a very bad idea (uses up the drive, they say). 

So now I would like to deactivate it. I don't want to just boot into the Live environment and simply delete the thing, because I'm assuming you have inactivate it within Linux itself (otherwise it's going to look for it, and be surprised when it isn't there). How do you do that?

My /etc/fstab currently looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=65c53c6f-6d5e-4c3e-baee-3b9a80630a69 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=000cee35-cd3c-47fe-ad35-02bc2b75e1a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

```

(i've no idea what those two /media/cdroms are, as I don't have a cdrom or a /dev/scd. But I suppose they aren't hurting) 

Is it enough that I simply comment out the line about swap? Do I have to do anything else? Or will that take care of it?

Any help greatly appriciated!

---

### Post by dargaud on 2009-04-07
First you can try "sudo swapoff" to see how your system runs without the swap file. Then you can comment the line in fstab.

---

### Post by Herman on 2009-04-07
I have an EeePC 4G and I have a swap file in mine instead of a swap area, I followed this how-to by iva2k, [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile").

I also turned swappiness to zero, [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") - Ubuntu Community Docs.

I installed using 'Manual Partitioning', and chose the Reiser file system because it is supposed to be ten to fifteen times faster for writing small files, (and operating systems and programs are mostly made out of small files).
Another thing about the Rieser file system is, we can easily type 'nolog' into the /etc/fstab line to turn off file system journalling. 

My EeePC performs great!

---

