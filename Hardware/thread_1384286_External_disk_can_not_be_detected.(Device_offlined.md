---
title: "External disk can not be detected.(Device offlined - not ready after error recovery)"
date: 2010-01-18
forum: Hardware
---

### Post by boblu on 2010-01-18
I have a 250G external hard disk which I had already formatted to ext3.
But every time I plug it, the dmesg shows this:

> [ 4287.549571] usb-storage: device found at 12
[ 4287.549575] usb-storage: waiting for device to settle before scanning
[ 4292.540767] usb-storage: device scan complete
[ 4292.541626] scsi 7:0:0:0: Direct-Access     WDC WD25 00JS-98NCB1      10.0 PQ: 0 ANSI: 4
[ 4292.542166] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 4292.547593] sd 7:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 4292.548853] sd 7:0:0:0: [sdd] Write Protect is off
[ 4292.548858] sd 7:0:0:0: [sdd] Mode Sense: 11 00 00 00
[ 4292.548862] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 4292.551524] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 4292.551531]  sdd: sdd1
[ 4292.560685] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 4292.560692] sd 7:0:0:0: [sdd] Attached SCSI disk
[ 4300.131274] usb 1-1: reset high speed USB device using ehci_hcd and address 12
[ 4310.400025] usb 1-1: reset high speed USB device using ehci_hcd and address 12
[ 4326.670021] usb 1-1: reset high speed USB device using ehci_hcd and address 12
[ 4326.950018] usb 1-1: reset high speed USB device using ehci_hcd and address 12
[ 4337.220024] usb 1-1: reset high speed USB device using ehci_hcd and address 12
[ 4337.375108] sd 7:0:0:0: Device offlined - not ready after error recoveryThere is actually a device added in /dev, named /dev/sdd and /dev/sdd1

But fdisk -l shows nothing about the external disk.

The external disk works well in Windows and Mac OS when it is formatted in ntfs. And when it is formatted in ntfs, it has the same problem under ubuntu.

Another thing is I am using soft raid1 in ubuntu box. Does this have any effect to the external drive?

Can anyone please tell why this is happened? and how to solve this problem?

---

