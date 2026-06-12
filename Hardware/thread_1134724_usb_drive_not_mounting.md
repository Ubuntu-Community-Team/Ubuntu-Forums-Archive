---
title: "usb drive not mounting"
date: 2009-04-23
forum: Hardware
---

### Post by donpdonp on 2009-04-23
I did an upgrade from 8.10 to 9.4. USB flash drives dont mount any more. Or any USB mass storage for that matter.

[10369.956066] usb 1-3: new high speed USB device using ehci_hcd and address 6
[10370.089554] usb 1-3: configuration #1 chosen from 1 choice
donp@sparky:~$ 

lsusb shows the device, but ubuntu does not do anything else.

---

### Post by emili01234 on 2009-06-20
> **donpdonp said:**
> I did an upgrade from 8.10 to 9.4. USB flash drives dont mount any more. Or any USB mass storage for that matter.

[10369.956066] usb 1-3: new high speed USB device using ehci_hcd and address 6
[10370.089554] usb 1-3: configuration #1 chosen from 1 choice
donp@sparky:~$ 

lsusb shows the device, but ubuntu does not do anything else.

I have the same problem, I tried everything but still can't mount my pendrive.

---

### Post by StijnVermeeren on 2009-07-04
Same problem here.

When I plug in my LaCie external hard drive, nothing happens.

dmesg just gives
```
[  438.256095] usb 1-7: new high speed USB device using ehci_hcd and address 3
[  438.389310] usb 1-7: configuration #1 chosen from 1 choice

```
and the device does not appear in "fdisk -l"

I'm using Ubuntu 9.04. In 8.10 it worked well.

On my brother's laptop with 9.04 it also works well!
"dmesg" on my brother's laptop gives:
```
[ 2080.137070] usb 2-3: new high speed USB device using ehci_hcd and address 3
[ 2080.568933] usb 2-3: configuration #1 chosen from 1 choice
[ 2080.575320] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2080.576830] usb-storage: device found at 3
[ 2080.576835] usb-storage: waiting for device to settle before scanning
[ 2085.572894] usb-storage: device scan complete
[ 2085.641033] scsi 7:0:0:0: Direct-Access     FUJITSU  MHY2250BH             PQ: 0 ANSI: 2 CCS
[ 2085.652044] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 2085.664056] sd 7:0:0:0: [sdc] Write Protect is off
[ 2085.664060] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 2085.664063] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 2085.676142] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 2085.684042] sd 7:0:0:0: [sdc] Write Protect is off
[ 2085.684046] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 2085.684049] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 2085.684056]  sdc: sdc1 < sdc5 sdc6 sdc7 sdc8 sdc9 sdc10 >
[ 2086.281984] sd 7:0:0:0: [sdc] Attached SCSI disk
[ 2086.283517] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 2088.996196] kjournald starting.  Commit interval 5 seconds
[ 2088.996767] EXT3 FS on sdc5, internal journal
[ 2088.996784] EXT3-fs: mounted filesystem with ordered data mode.
```

Apparently my Ubuntu doesn't even recognize that the thing I plugged in is a mass storage device?

Any ideas?

---

### Post by emili01234 on 2009-07-04
I think is a problem with usb 1.1 devices. I have read a thread that say the problem is solved disabling the echi_hcd module. But since now is part of the kernel, can't be disabled. Can be like that?

My pendrive is listed in 'lsusb' but not in 'fdisk -l' nor '/proc/partitions'.

If somebody knows how to solve this issue, please answer.

---

