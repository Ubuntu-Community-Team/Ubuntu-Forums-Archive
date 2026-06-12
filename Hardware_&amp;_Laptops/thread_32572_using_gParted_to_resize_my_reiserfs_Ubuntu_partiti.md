---
title: "using gParted to resize my reiserfs Ubuntu partition...?"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by simianMiscreant on 2005-05-08
I'd like to take 10gb out of my 35gb Ubuntu partition (reiserfs). It seems gParted would do this...it's just that my partition is greyed out when I enter the program. This would make sense - I can't resize it while it's mounted, right? So then do I unmount it *while in Ubuntu?* That seems crazy to me - am I going to have to resize it from another partition? I can't from Windows, can I?  :-| Please tell me if it's safe to unmount and resize my partition while in its operating system.

---

### Post by Martin Witte on 2005-05-08
I did resize (ext2/3, fat32, ntfs) partitions with parted via the detour of parted on the system rescue cd ([http://www.sysresccd.org)](http://www.sysresccd.org)). I have no experience with reiserfs though

---

### Post by simianMiscreant on 2005-05-08
My question is whether or not I can unmount the partition currently mounted to / in order to resize it...GParted shows my Linux partition as grey, and when I right-click it to view the possible operations, "unmount" is one of them. It won't let me resize m NTFS partition until I unmount it either, so I figure once I unmount my reiser one, it'll let me resize. I'd like to resize it, and I can't from Windows - resizing it in Linux seems to be my last hope.

---

### Post by Martin Witte on 2005-05-09
No - you can not unmout a drive while it is in use. Boot with a live cd - if you do not want to use the commandline version of the system rescue disk you could try e.g. Knoppix, it comes with qtparted.

---

### Post by az on 2005-05-09
You can also use the ubuntu installer cd and use it`s partitionner.

Just quit the installation after you resize your partition.

---

