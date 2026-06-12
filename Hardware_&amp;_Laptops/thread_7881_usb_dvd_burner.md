---
title: "usb dvd burner"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by jaba on 2004-12-12
I've been searching the forum for clues. Have got some, but none really solved the problem. 
The problem is finding/mounting my usb dvd burner, and in turn use it with k3b. I can't find out what device it's been given. I had an harddisk in the same usb-housing and found it as /dev/sda1. But it uses the mass storage driver, right? 

'dmesg' says:
```
usb 3-8: new high speed USB device using address 3
scsi6 : SCSI emulation for USB Mass Storage devices
  Vendor: _NEC      Model: DVD_RW ND-3500AG  Rev: 2.16
  Type:   CD-ROM                             ANSI SCSI revision: 02
Attached scsi generic sg0 at scsi6, channel 0, id 0, lun 0,  type 5
USB Mass Storage device found at 3
```

Then trying: 
```
[root@marwen]$ mount /dev/sg0 /mnt/tmp/
mount: /dev/sg0 is not a block device
```

'cdrecord -scanbus' 
```
 Linux sg driver version: 3.5.31
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus6:
        6,0,0   600) '_NEC    ' 'DVD_RW ND-3500AG' '2.16' Removable CD-ROM
        6,1,0   601) *
        6,2,0   602) *
        6,3,0   603) *
        6,4,0   604) *
        6,5,0   605) *
        6,6,0   606) *
        6,7,0   607) *
```

Tried mounting /dev/sdf and /dev/sdf1. But it's not a block device.

'mount' says:
```
usbfs on /proc/bus/usb type usbfs (rw)
```


Would be very thankful for tips and ideas.

---

