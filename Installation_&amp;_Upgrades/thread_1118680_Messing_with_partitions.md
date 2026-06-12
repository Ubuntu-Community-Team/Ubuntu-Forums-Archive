---
title: "Messing with partitions"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by winol5 on 2009-04-07
Hey,

Yesterday I resized my ubuntu partition in theory to give more soace to xp (yeah I know I'm a barbarian but I needed the space and ubuntu doest use a lot...so) but the swap partition didnt help, because i couldnt move it, so I just made a new partition (ntfs) with the free space after resizing ubuntu, the question is if I could add this patition to the xp original one so the swap one its just beside the ubuntu one

[[IMG]http://img408.imageshack.us/img408/1756/partitons.th.png[/IMG]](http://img408.imageshack.us/img408/1756/partitons.png)

---

### Post by Mark Phelps on 2009-04-07
Basically -- no.  You can't merge partitions that are separated by other partitions, plus, your second NTFS partition is inside an Extended partition, the first NTFS partition is not.

To combine the space, you would have to do the following:
1) Remove the second NTFS partition
2) Move the partitions inside the Extended partition to the right
3) Move the start of the Extended partition to the right
4) Extend the size of the first (and now, only) NTFS partition to fill the now unallocated space.

---

### Post by winol5 on 2009-04-07
how do I umount the swap one? in the live cd it shows with a key, BTW... what's an extended aprtition? I dodnt make it when I have done the partition setup

---

### Post by Mark Phelps on 2009-04-07
I've found that the best way to mess with partitions is to download the GParted LiveCD, burn it, and boot from that.  That way, you not only get the most current version, you also don't have to worry about any partitions being mounted.

You can get it from distrowatch.com website.

Look at your own screen shot.  You will see the second partition is Extended.

---

### Post by winol5 on 2009-04-07
I ahve been using the ubuntu livecd, I think i will download de gparted one, but the swap shows with a key when using the ubuntu livecd (the screenshot have been taken with native ubuntu running) I yeah I know I have an extended one, but what does that mean? is it that the  ntfs one is the primary or what?

Thx =D

---

### Post by Mark Phelps on 2009-04-07
It shows with a key because it's probably mounted and using the swap partition.  When you boot from the GParted LiveCD, it won't mount the swap partition.

An Extended partition is a partition that can nest other partitions inside of it.

---

