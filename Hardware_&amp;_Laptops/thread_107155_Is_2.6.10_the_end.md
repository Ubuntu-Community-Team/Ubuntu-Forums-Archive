---
title: "Is 2.6.10 the end?"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by km4hr on 2005-12-22
After upgrading my "hoary" system to "breezy" it wouldn't boot. Looks like Linux kernel version 2.6.12 is the culprit. My scsi/raid drives are not detected.  If I choose kernel version 2.6.10 during boot everything works fine. What does this mean? Is my scsi subsystem no longer supported? Does this mean that I'm stuck a 2.6.10 forever or is there some reasonably simple way to get my scsi drives to be recognized under 2.6.12? How long will I be able to run 2.6.10? Can I perform future software updates without updating the kernel?

System Description:

HP Netserver LXr 8000
Dual Pentium II Xeon 450
NetServer Rack Storage/12
HP NetRaid -3Si
MegaRAID, 438
Symbios Logic SYM53C896 (?)

thanks,

---

### Post by randy on 2005-12-24
The kernel configuration file may have been changed.  You should be able to take your 2.6.10 config and use it to build a newer kernel and then you can use that kernel to run your system.

---

