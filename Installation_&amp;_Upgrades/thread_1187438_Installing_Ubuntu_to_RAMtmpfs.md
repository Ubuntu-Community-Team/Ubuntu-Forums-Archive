---
title: "Installing Ubuntu to RAM/tmpfs?"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by ragtag on 2009-06-14
I've been playing with Puppy linux, a live cd that installs to tmpfs, and you can then run without the cd or a hard drive. What I like about it is that the performance is amazing. Programs start up instantly and everything is extremely snappy (except for the boot that needs to copy the system from cd to RAM). You can also save any changes to disk when you shut down, so that you can restore any changes you do or programs you've installed. While all this is nice, Puppy is not nearly as feature rich as Ubuntu, and you would need to do a lot of compiling and messing around to get things like graphics driver and Blender running. :)

I figure that there must be a way to do the same with Ubuntu. Copy the system to tmpfs before boot, and then running from that. I can easily afford using 1-2 gig for the tmpfs. And copy the tmpfs to disk on shut down.

Googling I didn't find much info no this, so anyone have any ideas how to do this?

---

### Post by Mighty_Joe on 2009-06-16
Puppy Linux is very stripped down compared to Ubuntu.  It is a 100Mb download compared to 631Mb for Xubuntu (the "light" Ubuntu).  There's a trade off between "feature rich" and the ability to be fit the entire OS into memory.

---

### Post by julianb on 2009-11-03
However, if you wanted some of the benefits of ubuntu (I love how easy it is to get Ubuntu to work with a wide variety of software and hardware) and some of the benefits of puppylinux, there's gotta be a way without totally re-working ubuntu.

Ubuntu installations can be far lighter than Xubuntu if you start out with the minimal CD, and then install your favorite packages out of the ones used in distributions like:
Masonux (a non-Canonical Ubuntu project)
PuppyLinux
DamnSmallLinux

...
I don't know anything about using tmpfs, but I'd love to learn, and I do know how to get an ubuntu system that uses barely any hard drive space.

---

### Post by Charlemagne1st on 2009-11-20
Getting Ubuntu to run from RAM is a very good idea - provided you have enough RAM. 1GB+ will do. 

This article explains how to do it:


[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

---

