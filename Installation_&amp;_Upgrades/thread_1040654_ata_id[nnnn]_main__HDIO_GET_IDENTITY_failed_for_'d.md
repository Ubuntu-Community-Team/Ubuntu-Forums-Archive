---
title: "ata_id[nnnn]: main : HDIO_GET_IDENTITY failed for '/dev/.tmp-8.0'"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by ejain on 2009-01-15
This message appears twice while starting up a fresh Ubuntu 8.10 64-bit server install. Doesn't seem to affect anything, but I'm curious what is causing this error message, and if there is a way to suppress it. What's a /dev/.tmp device? Doesn't show up after booting... The following may be relevant:

```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris
```

```
$ sudo ls -hal /dev/sd*
brw-rw---- 1 root disk 8, 0 2009-01-13 16:27 /dev/sda
brw-rw---- 1 root disk 8, 1 2009-01-13 16:27 /dev/sda1
brw-rw---- 1 root disk 8, 2 2009-01-13 16:27 /dev/sda2
brw-rw---- 1 root disk 8, 5 2009-01-13 16:27 /dev/sda5
```

---

### Post by arsnova on 2009-03-05
Nice and easy 'bump.'

I also have this failed ata_id message at boot for:

   /dev/.tmp-8-0
   /dev/.tmp-8-16

I'm running software RAID 1 under Ubuntu 8.10, nothing 'seems' buggy, but what are the risks associated with the error? I would love to have peace of mind before going into production.

Thanks!

---

### Post by 007casper on 2009-07-20
After I did the most recent update through update manager I reboot the computer.  Everything work without a problem.  After adjusting a few more things, I shutdown the server.  When I restart it, I got "/etc/mysql/debian.cnf error", and the server got stuck.  I shutdown once again.  When it was booting, it gave me "ata_id[1876]: HDIO_GET_IDENTITY failed for 'dev/block/8:0'" and it booted.  

I looked up a few places what this problem is and why/what it causes.  However, I cant seemed to find anything about it.  

I really appreciate anyone shedding light on this.  Thank you.

---

