---
title: "increasing hard disk space"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by faronicus on 2009-01-18
Hello,

I tried to go on the Ubuntu documentation area but I got a 404 error so I need help via the forum. 

I have installed Ubuntu alongside Windows OS, and Ubuntu only gave me about 15GB of space to work with. I'd like to increase it. How can this be done?

Help would be appreciated, and help in plain English would be appreciated even more. I'm not a programmer.

---

### Post by aheckler on 2009-01-18
You will need to use Gparted, a partition editor, to shrink the space on your drive for Windows and make more for Ubuntu. See thsi link for detailed instructions: [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by cdtech on 2009-01-18
If your running Windows XP you could just use the "Live CD" - open "gparted" and shrink the Windows partition and extend the Linux partition that way.

---

### Post by Mark Phelps on 2009-01-19
You didn't mention if your "Windows OS" is Vista.  If so, try to shrink the Vista partition first using Vista itself.  While GParted often works OK, in the few rare cases that it doesn't, it leaves your Vista partition unbootable -- which requires booting using Vista media to repair.

If you're using XP, you shouldn't have a problem shrinking the OS partition using GParted, or using the Partitioning tool inside Ubuntu.

---

