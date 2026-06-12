---
title: "Can't install 11.10"
date: 2012-02-18
forum: Hardware
---

### Post by gargaralarga on 2012-02-18
Hi.

I'm using 11.04 (no problem at all) but I tried to upgrade to 11.10 and the following messages appears,

The package 'dcp750cwlpr:i386' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?

So, I let to reinstall it or removed, but then appears the following message,

The package 'dcp750cwlpr:i386' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

So, I try to reinstall it but nothing changes and then I try to removed mannualy and it says,

Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Unable to locate package dcp750cwlpr-1.0.1-1.i386.deb
E: Couldn't find any package by regex 'dcp750cwlpr-1.0.1-1.i386.deb'

Later on it was told me that using nautilus I will have to erase all files associated to the printer and then I will have to try again. So I did it but nothing changes, the same message appears as before.

What can I do? Thanks!

---

### Post by LinuxFan999 on 2012-02-18
Upgrading through the update manager is not recommended.
 
Back up your data, then burn a CD of Ubuntu 11.10 and do a fresh install.

---

### Post by gargaralarga on 2012-02-18
Thanks, that is my last option. If there is no other way I'll do it

---

### Post by pedja_portugalac on 2012-02-18
> **gargaralarga said:**
> Thanks, that is my last option. If there is no other way I'll do it

Make new installation media, USB or CD and check its md5sum before burning. If it's OK reinstall fresh.

---

