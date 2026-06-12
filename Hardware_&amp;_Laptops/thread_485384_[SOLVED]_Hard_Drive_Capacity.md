---
title: "[SOLVED] Hard Drive Capacity"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by xDaveManx on 2007-06-26
I just installed a new hard drive and put Ubuntu 7.04 on it.

The drive was a Western Digital 320 GB IDE.  I realized there would be some discrepancy as to the stated size of the drive and the actual capacity, but I am coming up over 20 gigs short, depending on the method used to check used space.

GParted shows me coming up just under 300 GB total size.  It doesn't bother me that I lost around six percent of the capacity, but I am worried that I might have hit some sort of size limit and may run into some data loss.

What do you think?

A screenshot of GParted on my drive:

[IMG]http://i19.tinypic.com/4zxs5lv.png[/IMG]
[I]
Later...[/I]  Whoops, didn't realize this was the notebook only forum.  Mods, move if desired.

---

### Post by yabbadabbadont on 2007-06-26
ext3 filesystems, which you are using, have a journal that takes up space.  The larger the filesystem, the larger the journal.  That probably accounts for the discrepancy.

Edit: Add to that the fact that hard drive manufacturers use powers of 10 instead of powers of 2 when giving drive size.  So the listed size in linux will be smaller because of the different way it calculates a gigabyte (1,073,741,824 bytes as opposed to the 1,000,000,000 used by the drive manufacturers)

---

### Post by dabl on 2007-06-26
You're wasting about 4+ GB of space on that swap partition.  Regardless of how much RAM you have (I have 4GB), you won't ever need more than about 1GB of swap space.  Make it 1.5GB to be super safe.  But don't hold your breath waiting for it to be used..........   ;)

I'd partition it as follows:

/ = 10GB (set this "bootable" flag)
/{swap} = 1.5GB
/home = all the rest of it.

---

### Post by xDaveManx on 2007-06-26
Thanks, guys.  I suspected it had somthing to do with the different way of interpreting a Gigabyte, but wasn't sure.  In any case, it doesn't seem like I am going to run into any "bleed off" of data if I exceed the available space, like in the old days.

I didn't realize my swap partition was so big until I ran GParted.  I let Ubuntu do its thing when I installed it, so that came up on its own.  I have 2 Gigs of ram, and they say to double that, but I can't imagine a situation where I would need six Gigs of available RAM/Virtual memory.  I should be able to change that partition's size easily from the Live CD using GParted, right?

What are the advantages of having /Home on a separate partition?  When updating to a new version of Ubuntu, will I be able to install it to the / partition, leaving all my Home documents and settings intact for the new installation?

---

### Post by yabbadabbadont on 2007-06-26
> **xDaveManx said:**
> I should be able to change that partition's size easily from the Live CD using GParted, right? Probably.  Backup your personal files just to be safe though.

> **xDaveManx said:**
> What are the advantages of having /Home on a separate partition?  When updating to a new version of Ubuntu, will I be able to install it to the / partition, leaving all my Home documents and settings intact for the new installation?
Pretty much.  I reinstall a lot since I like to play with a bunch of different OS's and it is nice to have my personal settings/data readily available.

---

