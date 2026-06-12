---
title: "Hassle Free Disk Partitioning"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by hemlock on 2005-01-13
Hi,

I apologize if this question has been posed way too often. Didn't see it on the FAQ. 

What are my choices for disk partitioning programs? Given the grief some folks have had with parted, would is be preferable to partition first using some other program before installing ubuntu linux?

I have an AMD64 bit machine with 60Gb disk. I'd like to keep my Windows XP around, since my employer uses it. Sigh...

---

### Post by az on 2005-01-13
To make a short stopry long, the Ubuntu installer is based on the Debian installer.  When Warty was frozen (before it released) it was too late to include the very latest version of the installer which can handle NTFS partitions.

To shrink your windows partition, you need either
1-  The Hoary installer -  Just for the partitioning.  Stop and then run the Warty installer.
2-  the debian Sarge current installer.  You can download a 30 meg iso image for a netinstall.  This will suffice.  Again, stop after your drive is partitioned and start the Warty install with the Warty iso.
3-  Use a current version of Knoppix which includes QT parted (and ntfstools, I think) to partition your driver beforehand.

Yes, if you are running an NTFS partition, you will not be able to partition it with the Warty installer.

Hoary will be able to.

---

### Post by hemlock on 2005-01-15
Thanks for the reply. I have been unable to find the Hoary installation iso among the downloads. What am I missing?

I did manage to shrink the size of my Windows partition to make room for Ubuntu using the system rescue cd at [http://www.sysresccd.org](http://www.sysresccd.org).

---

### Post by socrazy143 on 2005-01-15
I used bootitng and it was a breeze.  They want $35 for the program but you can download it for free and use it without hassle.  It has different options for both CD bootable and floppy bootable.  I used the CD bootable and was able to shrink my XP partition quite easily.  The site for bootitng is:

[http://www.terabyteunlimited.com/](http://www.terabyteunlimited.com/)

---

### Post by hemlock on 2005-01-17
I installed ubuntu on my partitioned disk, and the following things occurred:

1) The X11 server seems to be misconfigured. My machine is a HP Pavilion zv5410us notebook.  /etc/X11/XF86Config identifies the graphics card as an "NVIDIA GeForce 440 Go 64M". That's nice, but it does not recognize the
display. It is identified as a "Generic Monitor". It is some kinda WXGA monitor. Default horiz and Vert refresh rates don't work with this monitor. Does anyone know the specs for this monitor? HP site was not helpful.

2) Looks like ubuntu warty clobbered by MBR so now I can't boot into WindowsXP. Instead the MBR points to my ubuntu partition and there is no mention of WindowsXP in the grub loader menu. How do I get ubuntu to recognize my windows partition and put it on the grub boot loaded menu?

---

