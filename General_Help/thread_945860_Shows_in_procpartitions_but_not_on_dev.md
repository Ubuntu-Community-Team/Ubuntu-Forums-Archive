---
title: "Shows in /proc/partitions but not on /dev/"
date: 2008-10-12
forum: General Help
---

### Post by gausie on 2008-10-12
Hi everyone

Got a device plugged in via USB. It shows up in dmesg, and also in /proc/partitions (sdb)

> major minor  #blocks  name

   8     0  244198584 sda
   8     1  238179658 sda1
   8     5    6016311 sda5
   8    16          0 sdb

How can I get it showing in /dev/? My goal is to wipe it completely.

Thanks

Gausie

---

