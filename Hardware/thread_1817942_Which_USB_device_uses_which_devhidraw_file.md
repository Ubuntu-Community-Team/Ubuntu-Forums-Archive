---
title: "Which USB device uses which /dev/hidraw file"
date: 2011-08-04
forum: Hardware
---

### Post by -jrosco- on 2011-08-04
Hi All,
 
I was wondering if anyone knew of a way to find out which device (e.g keyboard,  mouse, scanner) is using which /dev/hidraw character file. Need to know  where I could find this info, maybe something like lsusb or cat a file  in /proc to extract this info. I do not want to parse a log file I want a  cleaner way of archiving this.
 
System: Ubuntu 9.10
Linux: 2.6.31-22
 
Cheers
 
JC

---

### Post by -jrosco- on 2011-08-05
Got all the info I needed in /sys/class/hidraw/

---

