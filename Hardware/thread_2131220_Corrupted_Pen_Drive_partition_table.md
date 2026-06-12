---
title: "Corrupted Pen Drive partition table"
date: 2013-04-01
forum: Hardware
---

### Post by rabside on 2013-04-01
Hi guys,
I have a really big problem with my 32GB usb pen drive.
The Pen was formatted with ext3 and, when it was plugged in, the pc has had a power failure. result: corrupted partition table!

I tried to recover it, but I made a big mistake: with fdisk /dev/sda I chose the "create a new empty DOS partition table" option. Now Windows can see the pen drive with 0 byte and it can't format it. 
This is the output of my linux box when I plug it in:
```
usb 1-2: new high speed USB device using rt3xxx-ehci and address 3
usb 1-2: configuration #1 chosen from 1 choice
scsi1 : SCSI emulation for USB Mass Storage devices
scsi 1:0:0:0: Direct-Access              2303 PRAM        1.00 PQ: 0 ANSI: 0 CCS
sd 1:0:0:0: [sda] Attached SCSI removable disk
sd 1:0:0:0: Attached scsi generic sg0 type 0
```
and then 
```
fdisk /dev/sda
fdisk: can't open '/dev/sda'
```

do you have any ideas?
pls pls help

---

### Post by mechdave on 2013-04-01
Providing you don't write to the partition table you should have the drive with the ext3 partition still. Just make sure when you exit fdisk you DO NOT write the new partition table. If you have already done that, it is most likely good night to your data. If you are willing to say goodbye to your data just put another ext3 partition on it by sudo mkfs.ext3 /dev/sda BE CAREFUL though... It is using sudo which means GOD MODE :)

---

