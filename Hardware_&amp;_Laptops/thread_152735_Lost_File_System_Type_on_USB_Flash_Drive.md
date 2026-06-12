---
title: "Lost File System Type on USB Flash Drive"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by Joeb on 2006-03-30
My digital camera stores pictures on a smart media card which I then insert into a reader on the computer.  This last time, Ubuntu couldn't mount the drive, saying it couldn't detect the file system.  When I put the card back in the camera or a Windows PC, they both want to format the card.  Mac OS X shows gibberish, but does display the right number of files and size used.  Back in Ubuntu, opening the card (/dev/sda1) under gparted everything is normal except that it a) can't be mounted and b) there isn't a file system listed for the partition (which probably explains a).

Is there a way to write the file system type (umsdos) to the card without formatting or destroying the data?  I need to save these images if at all possible.

Joeb

---

