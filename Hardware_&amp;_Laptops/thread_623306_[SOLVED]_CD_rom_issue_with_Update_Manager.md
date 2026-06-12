---
title: "[SOLVED] CD rom issue with Update Manager"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by serhito on 2007-11-25
While trying to do an update through "update manager", I am getting the following message. I am new to Linux, so anybody could explain what i am supposed to do ?


cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by scrooge_74 on 2007-11-25
When you did your install the .deb packages you use came from the CD, the source list for repositories has the cdrom as a repository, just as if it was an internet address.

You can do it from inside synaptic and comment out the Cdrom since it is very likely you wont be installing from there after you have the system running.

You can also edit the file directly by opening a terminal and typing

sudo nano /etc/apt/sources.list

then the line which mentions the CD you put a # at the beginning of the line

---

### Post by serhito on 2007-11-26
You fixed my problem.
Thanks.

You must be frustrated answering such simple questions. :)

---

### Post by scrooge_74 on 2007-11-26
Nah, at one point I had simple questions too, anyway mark the thread as resolve so others can benefit. And keep posting questions someone will help

Have fun

---

