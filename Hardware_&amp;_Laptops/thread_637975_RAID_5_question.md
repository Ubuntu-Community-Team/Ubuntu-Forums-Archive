---
title: "RAID 5 question"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by helixfoil on 2007-12-11
I am building a home file server with ubuntu server 7.10 as the operating system. The hdd are going to be arranged:

80GB for the OS
500GB x4 for the samba server mounted

I am wondering if i use a software raid am i able to remove the OS disk and replace it and/or reinstall the OS am I able to just remount the array or do i lose my data. also since i created it in linux would i be able to possibly choose a different distro in the future and remount my array?

---

### Post by jexxie on 2007-12-11
> **helixfoil said:**
> I am wondering if i use a software raid am i able to remove the OS disk and replace it and/or reinstall the OS am I able to just remount the array or do i lose my data. also since i created it in linux would i be able to possibly choose a different distro in the future and remount my array?

You'll be able to remove the OS drive, and you'll be able to use the raid5 array in other Linux distributions, yes. (Should be automatically created if the raid5 kernel driver is installed.)

Cheers.

---

