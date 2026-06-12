---
title: "CD-RW won't burn, but will read"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by godfree2 on 2007-12-27
7.10
CD-RW known to be working, has been working under 7.04
no longer burns

xubuntu will read and mount disks
but it will not burn

xfburn
graveman
brasero
all report NO MEDIA
even when run as 'sudo'

cat /etc/fstab
..
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

ls
drwxr-xr-x  2 root root 4096 2007-12-21 11:47 cdrom0

dmesg
...
[  114.504000] attempt to access beyond end of device
[  114.504000] hdc: rw=0, want=68, limit=4
[  114.512000] attempt to access beyond end of device
[  114.512000] hdc: rw=0, want=1252, limit=4
[  114.512000] attempt to access beyond end of device
[  114.512000] hdc: rw=0, want=1028, limit=4
[  114.512000] UDF-fs: No partition found (1)
[  114.528000] attempt to access beyond end of device
[  114.528000] hdc: rw=0, want=68, limit=4
[  114.528000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[  485.200000] cdrom: This disc doesn't have any tracks I recognize!

---

### Post by vorondil on 2008-01-14
I too have the same problem.  Graveman posits that I have no media in the drive, when in fact I do.  Burning an iso with cdrecord from a terminal works just fine.  Perhaps a bug report is in order.

---

