---
title: "DCP-750CW pckg does not allow upgrade Ubuntu"
date: 2011-11-30
forum: Hardware
---

### Post by gargaralarga on 2011-11-30
Hi.

I'm using 11.04 (no problem at all) but I tried to upgrade to 11.10 and the following messages appears,

***The package 'dcp750cwlpr:i386' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?***

So, I let to reinstall it or removed, but then appears the following message,

***The package 'dcp750cwlpr:i386' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.***

So, I try to reinstall it but nothing changes and then I try to removed mannualy and it says,

[B][I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dcp750cwlpr-1.0.1-1.i386.deb
E: Couldn't find any package by regex 'dcp750cwlpr-1.0.1-1.i386.deb'[/I][/B]

What can I do? Thanks!!

---

### Post by jerrrys on 2011-12-01
have you checked your sources.list to see if any 11.04 sources have been carried over?  also could be a problem with any third party sources you carried over.  this package is not in the repository.

---

### Post by gargaralarga on 2011-12-08
Hi, Thanks. How can I check the source list? If the problem is the package itself, What can I do? I downloaded the package from the printer's web and I followed the installation instructions from there. Thanks again.

---

### Post by jerrrys on 2011-12-08
Open a terminal and enter:

gksudo nautilus

then (in nautilus root) click on "File System" and do a search on "dcp750"
and remove any leftover files.  Then try to upgrade to 11.10

[ATTACH]208734[/ATTACH]

After the upgrade you will need to go to the site and reload this "dcp" package.

And just for kicks, I would like you to post your "sources list" just to check for problems.  So again open a terminal and enter:

gedit /etc/apt/sources.list

and last, this upgrade should go fairly smooth.  But there are no guarantees.  11.10 runs on gnome3 only and your current install runs on gnome2.  Hope you have backup in place should it be needed.

---

### Post by gargaralarga on 2011-12-15
Thanks. Soo I finish the procedure I'll let you know if it works or not. About the upgrade you say something about backup, Why? I mean I've installed some some software such as MMA or Matlab, do I need to be re-install again those? Thanks again.

---

### Post by gargaralarga on 2012-02-18
Hi. I did what you told me, using nautilis I erase all files concerning the printer, but still says the same thing as before. What kind I do?

---

