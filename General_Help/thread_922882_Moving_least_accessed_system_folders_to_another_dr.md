---
title: "Moving least accessed system folders to another drive"
date: 2008-09-17
forum: General Help
---

### Post by Zero-g- on 2008-09-17
TL;DR : I want to move seldom accessed system folders to another drive, can I?

Hello everyone,
After a bit of lurking about this I can't seem to find anyone that has done this one. So, this might be interesting for your guys.

I have two drives in my comp. One is a solid state 4gb drive, the other is a 120gb WD Raptor.
I have installed the Ubuntu 8.04 to the solid state drive to let the system operate on critical files about an order of magnitude faster than a mechanical drive can handle.
The problem here is that space is limited and Ubuntu likes to get fat.
I need to know:
1. What folders on the root are the biggest space hogs or which ones are accessed less frequently. ex(in former terms): win\system32 is accessed often and much smaller, whereas Program Files is where things are installed but only has operations per program running from it.

2. Is it really safe just to make a symbolic link to a new folder on another drive and then copy the old folder into the new one? (sorry but to a recent convert this sounds way too easy.)

Thanks for the help.

---

### Post by Pro-reason on 2008-09-17
> **Zero-g- said:**
> 

2. Is it really safe just to make a symbolic link to a new folder on another drive and then copy the old folder into the new one? (sorry but to a recent convert this sounds way too easy.)

A symlink isn't the proper way to do it.  You should edit /etc/fstab so that the new partition is mounted at, say, /var.

---

### Post by Zero-g- on 2008-09-17
The new partition is already mounted as /home though it doesn't have to be. My desired end state is an ideal file system for a very responsive OS no matter what I'm doing with other programs.Unfortunately, I'm making it up as I go as far as linux is concerned. Any protips on the ideal setup would be greatly appreciated. :)7

---

