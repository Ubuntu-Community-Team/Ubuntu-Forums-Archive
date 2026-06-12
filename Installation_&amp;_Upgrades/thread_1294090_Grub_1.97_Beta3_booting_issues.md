---
title: "Grub 1.97 Beta3 booting issues"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by jm2 on 2009-10-17
I have an hp G60-445DX notebook. Vista with dual boot Ubuntu 8.10. This works just fine.
 
I added a partition and put 9.10 beta Karma on it. Using 32-bit windows.
 
Now I can't get into windows without turning off the laptop, taking out the battery, pressing the powerbutton and then putting the battery back in. plug it in, and may in 1 or two attempts it will get pass the check file system or restart - incorrect shutdown.
 
I have to do this to get into 9.10 also on some occassions.
 
Any suggestions?
 
 
I have Windows info from check disk that it couldn't repair something.
Event name: Startup Repair V2
signature/sequence 01: Auto Failover
signature/sequence 02: 6.0.6001.18000.6.0.6001.18000
03: 3
04: 65537
05: unknown
06: bad patch
07: o
08: 3
09: wrpRepair
10: 1168
OS Ver 6.0.6001.2.1.0.256.1
local ip 1033

---

### Post by jm2 on 2009-10-18
update-grub2  as root 
 
 solved this for now! 
 
These pointed me in the right direction.
 
[http://www.ubuntu.com/testing/karmic/beta#GRUB%202%20by%20default](http://www.ubuntu.com/testing/karmic/beta#GRUB%202%20by%20default)

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by jm2 on 2010-01-26
I am now using Grub-2 Beta 4 
and the update-grub2 

no longer is solving my dual boot issues?

I don't always have 10 minutes to try to get my pc to boot into windows.

What else should I try?

thanks

---

