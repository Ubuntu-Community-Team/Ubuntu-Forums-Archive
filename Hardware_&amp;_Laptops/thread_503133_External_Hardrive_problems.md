---
title: "External Hardrive problems"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by Jose Consuervo on 2007-07-17
Okay, I have two computers, both running Kubuntu Fiesty. When I plug my external hardrive into my desktop, It doesnt auto mount, but i just mount it manually via command line. When I plug my hardrive into my laptop it doesnt auto mount, and it is not on fdisk -l. I cant figure out why its not there. 

Here is the dmesg | tail output right after i plug the hard drive in.
> jose@Casey-Laptop:~$ dmesg |tail
[70917.572000] sda: assuming drive cache: write through
[70917.572000]  sda: sda1
[70917.576000] sd 1:0:0:0: Attached scsi disk sda
[70917.576000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[71688.400000] usb 3-2: USB disconnect, address 3
[71698.712000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[71699.804000] usb 3-2: configuration #1 chosen from 1 choice
[71699.804000] scsi2 : SCSI emulation for USB Mass Storage devices
[71699.804000] usb-storage: device found at 4
[71699.804000] usb-storage: waiting for device to settle before scanning


Thanks for any help!

---

### Post by Jose Consuervo on 2007-07-17
Any Ideas?

---

