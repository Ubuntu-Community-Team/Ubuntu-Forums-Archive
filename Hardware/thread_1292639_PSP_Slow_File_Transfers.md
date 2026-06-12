---
title: "PSP Slow File Transfers"
date: 2009-10-16
forum: Hardware
---

### Post by jdralphs on 2009-10-16
Hello,

I've been trying to figure this out for a while without much luck.  I connect my PSP to my Laptop (Compaq F750US) via USB and I get a relatively slow transfer rate to the memory stick that tops out at 1.9MB/s.  When I connect the PSP to a Windows Machine (the same laptop before I loaded Ubuntu 9.04 on it) I get a much higher transfer rate.

From /var/log/messages:
```
Oct 14 23:32:10 pesto kernel: [ 6999.330301] scsi12 : SCSI emulation for USB Mass Storage devices
Oct 14 23:32:15 pesto kernel: [ 7004.330580] scsi 12:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
Oct 14 23:32:15 pesto kernel: [ 7004.337851] sd 12:0:0:0: [sdb] 7929856 512-byte hardware sectors: (4.06 GB/3.78 GiB)
Oct 14 23:32:15 pesto kernel: [ 7004.342565] sd 12:0:0:0: [sdb] Write Protect is off
Oct 14 23:32:15 pesto kernel: [ 7004.351216] sd 12:0:0:0: [sdb] 7929856 512-byte hardware sectors: (4.06 GB/3.78 GiB)
Oct 14 23:32:15 pesto kernel: [ 7004.352634] sd 12:0:0:0: [sdb] Write Protect is off
Oct 14 23:32:15 pesto kernel: [ 7004.352663]  sdb: sdb1
Oct 14 23:32:15 pesto kernel: [ 7004.355953] sd 12:0:0:0: [sdb] Attached SCSI removable disk
Oct 14 23:32:15 pesto kernel: [ 7004.356137] sd 12:0:0:0: Attached scsi generic sg2 type 0
Oct 14 23:35:14 pesto kernel: [ 7183.908476] usb 1-4: USB disconnect, address 5

```

From lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 054c:01c8 Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Nautilus is reporting the following information for the memory stick:
```
Mount Point:  /media/disk
Filesystem:  vfat
Mount Options: rw nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8 flush
```

Anyone have any ideas how I can get resolve this speed issue?

Thanks!

---

