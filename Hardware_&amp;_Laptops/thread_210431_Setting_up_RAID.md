---
title: "Setting up RAID?"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by sludge99 on 2006-07-06
I was wondering if it is possible to mirror a partition in ubuntu

My partitions current look like this

Disk 1(sata) 70gb holds windows and linux partitions and boot stuff

Disk 2(ide) 115gb a 25 gb partition and then unused space

Disk3(ide) 190gb a 100gb partition and then a 90gb partition

i would like to mirror the 90gb partition on disk 3 on to the unused space on disk 2.  but idealy would like this to work in both windows and linux. i prity sure i could do this on windows with dynamic disks but dout that would work on ubuntu ? my mother board has a Nvidia nforce raid but it looks like it can only work with the whole disk not a partition. 

thought id ask if it could be done before i started messing around if any 1 could point me to a solution that'd be great

---

### Post by sludge99 on 2006-07-07
looking at this thread i not sure i posted it in the right section but not sure were else i could put it

but anyway i was thinking of programming a solution myself in linux to use fam(file access monitor) to detect when ever a file is modified and then copy to the other directory and create a similar program in windows

could also be useful to automatically back data up from my usb disk when i plug it in

but if any one can think of another way that'd be great

---

