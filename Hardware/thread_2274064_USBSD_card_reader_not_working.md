---
title: "USB/SD card reader not working"
date: 2015-04-17
forum: Hardware
---

### Post by optical2 on 2015-04-17
it works in an old xp machine, and on my friend's win7 machine, but not on my ubuntu machine.

# uname -a
Linux vps 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
#

[  127.352430] usb 1-1: new high-speed USB device number 2 using ehci-pci[  127.492545] usb 1-1: New USB device found, idVendor=0bda, idProduct=0119
[  127.492556] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  127.492562] usb 1-1: Product: USB2.0-CRW
[  127.492567] usb 1-1: Manufacturer: Generic
[  127.492571] usb 1-1: SerialNumber: 20090815198100000
[  127.495088] usb-storage 1-1:1.0: USB Mass Storage device detected
[  127.495261] scsi3 : usb-storage 1-1:1.0
[  128.496288] scsi 3:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[  128.496974] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  135.658560] sd 3:0:0:0: [sdc] Attached SCSI removable disk

# fdisk /dev/sdc
fdisk: unable to open /dev/sdc: No medium found
#

now, there actually is an NTFS partition on the physical SD card that I put on the SD card using anoter PC's internal SD card device.  Also tried using a FAT32 partition.  But while ubuntu looks like it sees the physical /dev/sdc device, not only can it not see a partition, it cant even use fdisk on the /dev/sdc

weird.  any ideas?  also doesnt work on puppy linux

---

