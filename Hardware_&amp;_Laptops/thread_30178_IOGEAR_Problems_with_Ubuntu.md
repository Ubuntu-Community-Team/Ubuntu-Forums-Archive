---
title: "IOGEAR Problems with Ubuntu"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by Justin Shreve on 2005-04-27
I've recently moved from gentoo, to install ubuntu, and I've come across a hardware problem I didn't come across before.

I bought a IOGEAR hard drive a few weeks back, and was able to find the device name (in /dev) on gentoo, by simply turning it on and looking in the logs (**tail /var/log/messages**). 

When doing it on this system I also get a path, which reads as: 

```
Apr 27 15:30:29 localhost kernel: SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
Apr 27 15:30:29 localhost kernel: SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
Apr 27 15:30:29 localhost kernel:  /dev/scsi/host5/bus0/target0/lun0: p1
```

So yes, I know it is reading the device.

Though /dev/scsi/host5/bus0/target0/lun0/disc, and /dev/scsi/host5/bus0/target0/lun0/part1 don't exisit (like the path's did on gentoo), nor is there anything even releated to /dev/scsi.

Just a few minutes before posting this, I noticed sdb, and noticed the devices /dev/sdb and /dev/sdb1, though I'm not able to view the partition table with fdisk -l, nor being able to mount it to a mount point. The sdb devices seem to dispear from /dev after a shortwhile.

Any ideas?

---

