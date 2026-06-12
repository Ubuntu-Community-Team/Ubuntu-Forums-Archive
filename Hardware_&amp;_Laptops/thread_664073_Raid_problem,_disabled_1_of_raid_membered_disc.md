---
title: "Raid problem, disabled 1 of raid membered disc"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by zero-Q on 2008-01-10
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110245](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110245)

I ve raid issues since 7.04. and yesterday I tried 8.04alpha2 and still same issue:) .whenever I boot ubuntu from live cd or instaled on other hdd, 1 of membered raid0 hdds goes to offline. 
after dmraid installed, I got this error msg.
"root@ubuntu:~# dmraid -ay
ERROR: isw device for volume "Volume0" broken on /dev/sda in RAID set "isw_cgffbhhfed_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_cgffbhhfed_Volume0" [1/2] on /dev/sda"

on the other hand, this problem does not depends on dmraid because with ot without dmraid 1 of the hdds goes offline and to make it online I must shutdown pc :).

well indeed I wonder that while I was using 6.10 without any problem on same raid setup, why ve I had this problem since 7.04? what was changed?

---

