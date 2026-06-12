---
title: "save hard disk via usb-connection with Gddrescue"
date: 2014-03-21
forum: Hardware
---

### Post by Bronvu on 2014-03-21
The hard disk of my laptop crashed and I want to recover exactly one file. The rest was either backed up or unimportant, but i missed this one file.

I replaced the crashed hard disk with a new one and reinstalled Ubuntu, and now i've connected my crashed hard disk with an usb-adapter.

lsblk gives:
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 462.8G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0     3G  0 part [SWAP]
sdb      8:16   0 232.9G  0 disk 
&#9500;&#9472;sdb1   8:17   0 229.9G  0 part 
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0     3G  0 part 
sr0     11:0    1  1024M  0 rom  

So it seems that the crashed hard disk is reconised (the 250GB one).

I've installed the Gddrescue and tried to copy an image with the following command:
*ddrescue -d /dev/sdb /home/bronvu/Documents/image.img /home/bronvu/Documents/logfile.logfile*

Unfortunatly I get the following error: * ddrescue: Can't open input file: Permission denied*

What am I doing wrong? Is it even the correct approach, or should I do it entirely different?
I've searched on the forum for a sollution, but i wasn't able to solve the problem yet...

Please help!

---

### Post by westie457 on 2014-03-21
Welcome.
Is it possible you forgot to put sudo at the front of the command?

---

### Post by Bronvu on 2014-03-21
Yes. Yes it is. 
:frown:
Thanks

---

