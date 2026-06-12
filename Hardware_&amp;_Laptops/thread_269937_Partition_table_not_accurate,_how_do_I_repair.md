---
title: "Partition table not accurate, how do I repair?"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by Giggity on 2006-10-02
So, in WinXP, using Acronis Disk Director Suite, I have a graphical map of my partitions on my main HDD that looks like this (description of what's on the partition in parentheses):

[LIST]
[*]Partition 1:  NTFS (39.06 GiB, Windows XP)
[*]Partition 2:  Ext3 (13.58 GiB, Ubuntu)
[*]Partition 3:  Linux-Swap (1.13 GiB, used by Ubuntu)
[*]Partition 4:  NTFS (about 36 GiB, where some Windows apps are installed)
[*]Partition 5:  Ext3 (about 100 GiB, where I was going to install Gentoo, and failed... which was the last thing I did before this all started)
[/LIST]

That's the way I want it.  But in Ubuntu's Disk Manager, I get something that's not quite what I was expecting (this is the order presented):

[LIST]
[*]Partition 1:  NTFS (39.06 GiB, Windows XP, like above)
[*]Partition 2:  Ext3 (13.58 GiB, Ubuntu [in use as I write this post], but Disks Manager says nothing's going on here)
[*]Partition 5:  Unknown filesystem (1.13 GiB, it's what should be being used as my swap right now)
[*]Swap Partition:  Memory Swap (36.10 GiB, where NTFS Partition 4 reported by Windows should be)
[*]Free Space:  Not Partitioned (100.4 GiB, where Ext3 Partition 5 reported by Windows should be)
[*]Partition 3:  Ext3 (4.88 GiB Free, I have no idea where this came from)
[/LIST]

This started after I tried and failed to install Gentoo (said something about not being able to mount the partition that I wanted to install to).

Does anyone know how I can get this all back in order?  I'm pretty sure that the map offered by Disk Director in Windows is the correct one, as that's what Ubuntu used to show.

---

### Post by Giggity on 2006-10-02
Okay, sorry for bugging y'all, but I figured out the solution to this problem while in the middle of typing it out.  I decided I would just go ahead and post it along with how I solved it for future reference by anyone else having a similar problem.  It's fairly simple, although I don't know exactly what caused it.

I used to have a main hard drive (SDA) that looked like this:

[LIST]
[*]Partition 1: NTFS (39.06 GiB, Windows XP, recognized as /dev/sda1)
[*]Partition 2: Ext3 (13.58 GiB, Ubuntu, mounted as /dev/sda3)
[*]Partition 3: Linux-Swap (1.13 GiB, used by Ubuntu, mounted as /dev/sda6)
[*]Partition 4: NTFS (about 140 GiB, where some Windows apps are installed)
[/LIST]
Then I chopped off about 100 GiB of free space from Partition 4 (where I wanted to install Gentoo):
[LIST]
[*]Partition 1: NTFS (39.06 GiB, Windows XP, recognized as /dev/sda1)
[*]Partition 2: Ext3 (13.58 GiB, Ubuntu, mounted as /dev/sda3)
[*]Partition 3: Linux-Swap (1.13 GiB, used by Ubuntu, mounted as /dev/sda6)
[*]Partition 4: NTFS (about 40 GiB, where some Windows apps are installed, recognized as /dev/sda5)
[*]Partition 5: Unpartitioned Free Space (about 100 GiB)
[/LIST]
Installing Gentoo did something to the device names, namely switching the identity of /dev/sda3 to /dev/sda2, as well as trading the names of /dev/sda5 and /dev/sda6.  How Rude!

So, anyway, just running "kdesu kate /etc/fstab" and then editing the mount devices to accurately reflect their new names has done the trick.

---

