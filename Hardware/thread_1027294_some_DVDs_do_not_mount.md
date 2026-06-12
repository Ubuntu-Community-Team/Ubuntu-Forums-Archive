---
title: "some DVDs do not mount"
date: 2009-01-01
forum: Hardware
---

### Post by VinisLentoje on 2009-01-01
Ok: Some burned data DVD disks won't open: I put the disk into the drive, wait, but nothing happens, can't access the disk no matter what I try, except that my Nero linux 3.5.1.0 can see the disk in the drive and it's track. I tried those DVDs on my other Ubuntu machine, and they worked fine.
I've tried mounting those DVDs manually, but I failed.
here's the "lshw -C disk":
  *-cdrom                 
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready


Any ideas?

P.S. Ubuntu 8.10, but encountered this for the first time on 8.04

P.P.S. I tried searching for this problem, but I found nothing helpful, so if You know that this problem was posted somewhere, let me know.

---

