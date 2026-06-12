---
title: "Partitioning Advice Needed"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by kenmcfa on 2007-06-23
I will soon have a completely blank 80GB hard disk. I would like to use it to dual-boot Windows XP and a version of Ubuntu (I haven't yet decided whether to choose Ubuntu or Kubuntu). What sizes, positions and filesystems should my partitions have to best allow this?

---

### Post by finer recliner on 2007-06-23
see this thread:
[http://ubuntuforums.org/showthread.php?t=479456](http://ubuntuforums.org/showthread.php?t=479456)

---

### Post by kenmcfa on 2007-06-23
Ok, thanks for that link, but how big should my linux partitions be?
Is this summary of the structure and sizes of my partitions ok?:

Partition 1: 55MB ext3 /boot (for GRUB)
Partition 2: As big as possible NTFS (for XP)
Partition 3: 5GB ext3 / (for Ubuntu)
Partition 4: 1GB SWAP (that's 2*my RAM)

Do I need a /home partition?

Also, at some point in the future I'd like to make my own bootloader. Should I do anything fancy with my partitions right now to allow for this?

---

### Post by wastedfluid on 2007-06-23
While I am too lazy to read the above article, I recommend doing this.

Creating a partition.. say, 20gb, for windows.  20gb NTFS partition.  Install the version of Winblows you would like.  Leave the other 60GB unallocated.

After you install Windows, with 60gb unallocated, boot off the Ubuntu cd with your flavor of choice.  Choose the option to "use the largest unallocated space" - and let Ubuntu set up your swap, and /.  GRUB will overwrite the existing bootloader Winblows uses, while letting you choose between Ubuntu and Windows on boot.

---

### Post by logos34 on 2007-06-23
Forget the separate /boot partition.  (unless you plan to add several more linux distros to the mix).
Make the windows partition however large or small you think you need it to be.  

> Do I need a /home partition?

Yes, I'd highly recommend it.  It makes a fresh install of a new release a jiify.  (your data and settings files on a separate /home partition remain untouched).

5GB is the minimum I would personally advise for ext3 / (root).  Might want to add a couple of gigs or more for good measure (depending on how much software you're planning on installing).  1GB swap should be just fine. (even if you double the ram, more than a gig swap on ubuntu is a waste IMO.  You don't have AV and all that other stuff running like in windows, hogging sys resources.

Get fs-driver for windows (read+write to ext3) and ntfs-3g for linux side (adds NTFS write capability to linux)

check out the ubuntu section at psychocats.net and the link to Herman's dual-boot page.

have fun and welcome to ubuntu!

---

