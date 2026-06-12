---
title: "HDD overheat!"
date: 2010-06-15
forum: Hardware
---

### Post by luismgl on 2010-06-15
60ºC +
Is this normal in ubuntu systems?
If not, help please.

---

### Post by dabl on 2010-06-15
Looks too hot for normal use.

System details, please.

---

### Post by luismgl on 2010-06-15
Intel Core i3 CPU   M 330  @ 2.13GHz, 4 GB - DDR3, hdd 320 GB SATA 7200rpm, runing on ubuntu 10.04

---

### Post by dabl on 2010-06-15
Desktop or laptop?  Fans working? 

Basically, you need to look at the airflow across the hdd. If your system is not a new one, maybe open it up and look for clogged air intake or filter/screen.

If you suspect there is something about Ubuntu that is causing the hdd to "work" too much, you could make a Live CD of another (non-*buntu) Linux distribution, and boot that one, and see if there is any difference.  Some choices:

- Mepis
- sidux
- Debian
- E-live
- Fedora 13

---

### Post by luismgl on 2010-06-15
Its a laptop, and the fan is working fine. The system is relatively new, about 4 months old, and there isnt anything blocking the air flow. Yea I think I will try a different OS

---

### Post by dabl on 2010-06-15
Also if you can determine the model of your hdd, check here to make sure it isn't subject to a known issue:

[https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux](https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux)

---

### Post by luismgl on 2010-06-15
didn't find it there, the hdd is a Toshiba MK3256GS

---

### Post by dabl on 2010-06-15
I only have a big desktop rig with WD hard drives, which run around 40 - 45C most of the time, and a Toshiba netbook which I've never bothered to install hddtemp on.

60C is hotter than I've seen a hard drive run.  I'd be worried -- I wouldn't keep my mission-critical data on that one.

I googled your drive model, and didn't find an exact match.  But, it looks like this one is very close:

[http://sdd.toshiba.com/main.aspx?Path=StorageSolutions/PCNotebookHardDrives/MKxx54GSYSeries](http://sdd.toshiba.com/main.aspx?Path=StorageSolutions/PCNotebookHardDrives/MKxx54GSYSeries)

According to that spec sheet, the max operating temp is 55C.  So yours is running over that spec.

---

