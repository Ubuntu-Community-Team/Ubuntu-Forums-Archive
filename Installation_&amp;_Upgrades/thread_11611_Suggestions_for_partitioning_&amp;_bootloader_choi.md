---
title: "Suggestions for partitioning &amp; bootloader choice?"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by nightmorph on 2005-01-18
Welll, my Ubuntu CDs were finally shipped to me. I promptly put aside the documentation I had been going through for the past several months and eagerly booted the installation CD. To make a long story short, the install has failed miserably. Not only does Linux hang while loading and my network card is completely unusable (Ubuntu doesn't even acknowledge my DHCP network), but I can't even boot Windows anymore without using an Ubuntu LiveCD.  

I'm thinking that maybe this has something to do with my bootloader and partitioning choices?

I selected Lilo, if only because it seems to been around the longest and thus most dependable.

My INTENDED partitioning scheme was something like this:

**hda1**: 7 GB Windows Millennium partition, FAT32, bootable, primary, with options set to use and read files from, etc. Added the "Quiet" option as well as the other option that's NOT "mount read only," on the off chance that I create a document in OOo and need to put it on my Windows partition. Sorry that I can't remember which option it is.
**hda5**: 500 MB swap partition, logical.
**hda6**: 4 GB Ubuntu partition, ReiserFS, also logical.
*******: The rest of the drive is unpartitioned free space; about 18 GB.

I put Lilo in the MBR as the directions suggested, as I was unsure if I needed a "/boot" partition or not.

I guess I really don't know where the problem is. I only included my windows partition (mounted under "/windows", theoretically) as I want to be able to read files if I'm using Ubuntu at the time. Does Ubuntu need to be on a primary partition? Do I need to use GRUB so that I can get an OS selection option when I turn on my laptop? I'd really like to be able to mount my Windows partition when I need it, and I want to retain a smart arrangement of Linux partitions; maybe there's an even better arrangement. I'm willing to hear suggestions on what kinds of partitions I should use.

I'm willing to try most anything on my next Ubuntu install later today; there's nothing that can be done from the system on the hard disk itself; it's completely nonfunctional. Well, it worked once, but Xfree couldn't load; there are hardware AND software issues. Time to wipe everything and start over...this time, hopefully the RIGHT way. I will say that the LiveCDs do let me access the internet and my network. I just wish the install CD worked as well as the LiveCD.

* Oh, and how would I go about removing Lilo from my MBR so that Windows can load normally for the brief time when it is the only OS on my hard drive? Or is this even an issue?

---

### Post by nightmorph on 2005-01-19
Never mind. After 11 consecutive failed install attempts, I finally got a basic Ubuntu system running, complete with (semi) working GUI.

Apparently, using the basic 2.4 kernel and ext3 as my file system worked when kernel 2.4 and reiserFS would not. Any time I tried to do anything with the 2.6 kernels, my system would not completely install. Or if it did, XFree86 could not load gdm. Or something like that.

Of course, even with the "successful" install, my USB mouse doesn't work... but that's for another forum.

At least Ubuntu has an attractive desktop.

---

