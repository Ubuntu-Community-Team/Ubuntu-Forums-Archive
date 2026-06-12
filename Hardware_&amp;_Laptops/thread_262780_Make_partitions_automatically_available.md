---
title: "Make partitions automatically available"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by Denoli on 2006-09-22
Hei! 

after following the manual on how to make a partition automatically available at boot. i have a smal problem. only the first disk is available. i have tryed and changing witch one is first. and the first one works no mather what disk it is.

i have 2 disk's i try to auto boot at start. using the code 

> 
/dev/sda5 /media/windows ntfs umask=0222 0 0
/dev/sdb5 /media/windows ntfs umask=0222 0 0


plz help

---

### Post by gosh on 2006-09-22
You mount the two drives to the same mount point (/media/windows)
How about:
			 				/dev/sda5 /media/windows1 ntfs umask=0222 0 0
/dev/sdb5 /media/windows2 ntfs umask=0222 0 0

---

