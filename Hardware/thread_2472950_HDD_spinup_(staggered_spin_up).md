---
title: "HDD spinup (staggered spin up)"
date: 2022-03-18
forum: Hardware
---

### Post by vesoljc on 2022-03-18
Hi all,
I have a home server setup: 
Ubuntu 20.04
MSI B250M PRO-VD
Celeron g3930
16gb ram
m2 for OS
3x wd red in mirror mdraid

I run a few services on it, samba share etc...

When there is no disc activty for a while those disks spin down and power off, which is ok, as I don't need them online 24/7. however, when a read/write request happens, those disks start to spin up. What bothers me is, that they do a staggered spin up, so one spins up, take a fews seconds, then the second, then the third. All in all it takes 10+ seconds. I did some reading about staggered spinup, I understand why it happens (power draw), but in my case I'd like to bypass it and have my disks spin up at once. But, I didn't find any real way on how/where to do it. Not sure whose domain this is (OS, drivers, bios)?

Would be thankful for any info/help!

Thanks,
marko

---

### Post by TheFu on 2022-03-18
**hdparm** can control some HDD settings. I think spindown can be disabled on many disks.  You'll need to check the manpage and since those settings are lost, you'll want to have them re-applied at every boot.

For any RAID array, allowing disks to spin down was a bad idea for a long time. Is that not still true?  I don't allow it on any of my mdadm RAID1 arrays. It would defeat the purpose of using RAID.

---

### Post by Yellow Pasque on 2022-03-21
Maybe: [https://wiki.archlinux.org/title/Improving_performance/Boot_process#Staggered_spin-up](https://wiki.archlinux.org/title/Improving_performance/Boot_process#Staggered_spin-up)

---

