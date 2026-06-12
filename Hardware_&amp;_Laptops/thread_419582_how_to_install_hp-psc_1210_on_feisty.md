---
title: "how to install hp-psc 1210 on feisty??"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by vliegje20 on 2007-04-23
I followed this topic: [http://ubuntuforums.org/showthread.php?t=121896&highlight=psc1210](http://ubuntuforums.org/showthread.php?t=121896&highlight=psc1210) for dapper drake. But in feisty when i do:
patrick@ubuntu:~$ hp-makeuri /dev/usblp0

HP Linux Imaging and Printing System (ver. 1.7.3)
Device URI Creation Utility ver. 4.3

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Device not found

i get that error. Can someone help me?

Edit: thread can be closed.

I did'nn do:
sudo apt-get install hplip hplip-data hplip-ppds hpijs foomatic-db-hpijs

so when i did that and installed it through HPLIP Toolbox it got the right pps driver and now it works

---

