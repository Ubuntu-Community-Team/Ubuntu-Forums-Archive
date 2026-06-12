---
title: "Copy data from a broken filesystem"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by mrgod on 2007-10-09
Hi!

I'll go straight to the case:
I got a 500GB ext2-partition with 200GB data on it. The disk is a 500GB WD. The filesystem on this disk is broken. I got another partition on a second disk that is 250 GB. My intention is to copy the 200GB data-part to the other disk(250GB partition). I've tried with the "dd-commando", but it stops when the 250GB partition is full.

Is there any way I can copy the 200GB data to an another disk, and try to restore it there? My plan is to make a image of the data, and then try to recover it.
Just need help to copy this data... :confused:

Any help will do :) Totally stuck on this one.

---

### Post by jnorthr on 2007-10-09
read someplace that there is a command called 'dd' that may let you gain access to particular portions of a partition, but please read the man pages first.

---

### Post by mrgod on 2007-10-09
> **jnorthr said:**
> read someplace that there is a command called 'dd' that may let you gain access to particular portions of a partition, but please read the man pages first.

Thanx for the reply. I have read the man-page, but there are a couple of terms I don't understand.. Countn't find anything obvious for the case.. can you help me out ? :)

---

### Post by Xenaco on 2007-10-10
You state that the filesystem is broken.  How do you know this?  What type of error are you getting or what program is reporting a broken filesystem?  If you use ***dd*** to copy a disk you will copy all data as it exists on the original disk, errors and all. A ***dd*** bit-for-bit copy of a device (/dev/[hs]dx) will copy everything including the partition **and** filesystem information.  A ***dd*** bit-for-bit copy of a filesystem (/dev/[hs]dx[1-xx] will copy everything including the filesystem information.

You may be able to fix your broken filesystem with the ***fsck*** command first.

---

### Post by az on 2007-10-10
If you want to copy a 500GB filesystem onto a 250 Drive, well, you can't.  Perhaps you can put it on a loop directory and then compress it, but that would require that you have the space to do that.

There is no way around it, you are going to have to buy another hard drive to image your disk.  Don'T try to fix your filesystem without imaging it first.  Make the image and then work on the image.

The other option is to data-carve the files out of the broken filesystem.

Use foremost or Photorec to recover files that way.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)


[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

