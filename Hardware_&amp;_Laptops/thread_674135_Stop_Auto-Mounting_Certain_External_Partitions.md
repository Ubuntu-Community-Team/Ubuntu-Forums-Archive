---
title: "Stop Auto-Mounting Certain External Partitions"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by webworldx on 2008-01-21
Hi Guys, 

I've got an external media recorder drive which automatically partitions itself with two LinuxUDF's, a disk and a disk-1 partition.  The main data store is held on the disk partition, whereas the others just have lost+found directories in them.  The entries do not appear in my etc/fstab/ as their mounted on the fly when the USB drive is plugged in, so I'm just wondering if there's an option/program that'll let me **only** mount the /media/disk/ partition and not the rest of them when the drive is turned on?

Cheers!

---

### Post by webworldx on 2008-01-26
- Bump -

Just in case anyone has an answer.  If not, is there any way I can get a reading of the current mounted drives so I can add it to the etc/fstab automatically on boot? And will this cause a problem if the fstab can't find the drive (i.e. it's not plugged in)

---

