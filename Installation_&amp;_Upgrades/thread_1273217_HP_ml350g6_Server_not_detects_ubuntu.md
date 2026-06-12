---
title: "HP ml350g6 Server not detects ubuntu"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by MaheshChowta on 2009-09-23
We are installing ubuntu Server 9.04 in

ProLiant ML350G6(Tower Model) / Hot Plug LFF Model/(1) Quad-Core Intel Xeon E5504Processor (2.0GHz, 80 Watts, )/ 4MB Level 3 cache / 4GB (2 x 2 GB) PC3-10600R (DDR3-1333) Registered DIMMS /Embedded NC326i Dual port  Gigabit Server Adapter / Smart Array P410i with no memory/  DVD ROM Drive/460 Watt Power Supply/ 4TB sata hard disks.

Installation went well. But after booting, Server not detects the operating system. We doubt, it is because of raid system.  How I can continue?

---

### Post by MaheshChowta on 2009-09-23
By installing lilo I solved this problem.

But, I am facing new problem.  
Lilo gives following message:

LILO 22.8 Load i Linux...............................
.............
.............
BIOS data check successful




[FONT="Courier New"]PANIC: early exception 0e rip 10:ffffffff80226aa3 error 0 cr2 ffffffffff5fc0f0
[/FONT]

How I can continue? Please Help me.

---

### Post by MaheshChowta on 2009-09-24
Ok, No replies.

Yesterday downloaded ubuntu i386.iso image and installed on this server. Now I am getting this error after LILO boots linux


BUG: Int 14: CR2 ffffb0f0 ............... 

STACK: 


--------------- 

How I can continue?

---

