---
title: "USB memory sticks are not mountable in Jaunty"
date: 2009-04-22
forum: Hardware
---

### Post by rcc on 2009-04-22
When I changed to Jaunty, the USB memory sticks are not mountable.  I try to mount them, and the mount fails. They are seen by lsusb, which reports:
$ lsusb
Bus 001 Device 006: ID 03f0:3207 Hewlett-Packard 
Bus 001 Device 005: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 004: ID 07cc:0500 Carry Computer Eng., Co., Ltd Mass Storage
Bus 001 Device 003: ID 04a9:1709 Canon, Inc. PIXMA MP150 Scanner
Bus 001 Device 002: ID 05e3:0660 Genesys Logic, Inc. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Device 006 and 005 are obviously the sticks I want to mount, but I can't seem to mount them.  The is the automount for USB sticks gone?

---

### Post by cariboo on 2009-04-23
What is the output of:

```
dmesg | tail -n10
```

when you plug one of the devices in?

---

### Post by rcc on 2009-04-23
Dmesg output =

$ dmesg | tail -n10
[212058.168767] sd 14:0:0:0: [sdh] Write Protect is off
[212058.168771] sd 14:0:0:0: [sdh] Mode Sense: 23 00 00 00
[212058.168775] sd 14:0:0:0: [sdh] Assuming drive cache: write through
[212058.171452] sd 14:0:0:0: [sdh] 7827456 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[212058.171947] sd 14:0:0:0: [sdh] Write Protect is off
[212058.171950] sd 14:0:0:0: [sdh] Mode Sense: 23 00 00 00
[212058.171953] sd 14:0:0:0: [sdh] Assuming drive cache: write through
[212058.171957]  sdh: sdh1
[212058.214868] sd 14:0:0:0: [sdh] Attached SCSI removable disk
[212058.214959] sd 14:0:0:0: Attached scsi generic sg8 type 0

---

### Post by Bateluer on 2009-04-23
Is anyone else experiencing issues with mounting USB drives? I wish to nuke my Windows partition entirely and move to using Ubuntu as my sole OS, but I kinda need my USB thumb drives to work.

---

### Post by And1945 on 2009-04-25
Im having sort of the same problem. Sometimes it wants to, other times not

My biggest issue right now, is that It does not want to mount a storage partition (not root or home or anything).

so, yes... I know your issue. Just dont have a fix unfortunately.

---

