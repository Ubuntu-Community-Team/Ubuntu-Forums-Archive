---
title: "Unable to unmount the CD-ROM"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by frisket on 2007-03-10
I'm trying to add build-essential and its dependencies to a newly-installed Edgy on an Inspiron 2500 in order to get the network card working (so there is no network connection right now).

/etc/apt/sources.list shows the cdrom as the first deb entry, and when I try sudo apt-get install build-essential it finds all the dependencies and then asks for the Edgy 6.10 CD to be inserted, but when I insert the disk and hit Enter, it says "Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/pool/..." followed by the correct path to the first package, then "Unable to unmount the CD-ROM in /cdrom/, it may still be in use." and it repeats this for each package it wants.

Why is it trying to unmount the CD-ROM? The CD icon is on the screen, so it has correctly recognised and mounted it. Is it because the CD-ROM was auto-mounted as me, so root thinks it can't grab it. And how do I run apt-get in this state?

---

### Post by frisket on 2007-03-10
Forget it...I installed from the Alternative CD, and it turns out that that means you have to use that exact one when running apt-get...duuuh

---

