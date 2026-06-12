---
title: "format in mac"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by willfriedwald on 2009-03-26
is there any way I can use Gparted (in Ubuntu) to initialize a new drive in the MAC format?  Am copying a bunch of music from a Linux machine a drive to be used on a Mac system machine.

Any clues?

thanks!

Willfriedwald

---

### Post by Pumalite on 2009-03-26
You can use it. Make the format vfat (Fat32)

---

### Post by willfriedwald on 2009-03-26
right!  thank you.

I know the Mac CAN read FAT32, but is there anyway to format it (via ubuntu) into the Mac format? 

I know the Mac can read the DOS format, but since this drive is going to be a permanent addition to the Mac, I would prefer to initialize into Mac format - if it can be done on the linux platform...

failing that, I will just format it on the MAC, then move it to the linux, hopefully the linux will be able to copy to it (I sometimes have pesky problems with permissions) and fill it on the linux, then move it back to the mac...

thanks!

W

---

### Post by damis648 on 2009-03-26
The Mac filesystem is HFS+. The current set of HFS+ tools in ubuntu doesn't allow for creation of HFS+ partitions. You will have to do it on a Mac. Just use disk utility, and format as 'Mac OS Extended'. (Do NOT use journaled, as Ubuntu cannot write to journaled HFS+).

---

### Post by willfriedwald on 2009-03-26
no JOURNALED? well THAT'S good to know- that's probably what's been screwing me up all this time!

thanks!


w

---

### Post by NiN on 2009-03-26
I wouldn't recommend using hfs+ in combination with linux. Tried it myself and ended up with strange problems (linux detecting the drive as faulty and mounting readonly) after a few weeks without proper ways to fix it.  You can use macfuse ([http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)) on your mac to access windows NTFS drives and the linux utilities are also way more advanced for that filesystem. (in contrast to hfs+) and at least it does not have the annoying limitations of fat32.

---

### Post by lalawawa on 2009-03-28
I was able to format a disk as FAT32 on linux, but can't figure out how to mount it.  "mount -t fat ..." and "mount -t vfat ..." don't work.

---

### Post by lalawawa on 2009-03-28
I should add that I'm trying to do the same thing that willfriedwald is trying to do, except I don't have the Mac yet, I am evaluating the feasibility of getting a Mac.  So I would like to format a Mac-readable drive and copy my music to it.

---

### Post by afrodeity on 2009-04-07
Are you sure this isn't simply a legal issue? The HFSPlus section of the [Gentoo Wiki]("dd if=tiger-x86-flat.img of=/dev/hdb2 bs=512 skip=63") was deleted, apparently because Apple threatened to sue or something? Although this could just be a rumour, I wouldn't put it past Apple to do something like this. Which is really dumb, because a lot of Mac users are duel booting with Ubuntu.

---

