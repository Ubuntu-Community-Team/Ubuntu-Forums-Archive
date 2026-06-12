---
title: "Recover lost sda partition"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by cimex on 2007-08-11
Ubuntu can no longer mount my USB, it seems as if I've lost my /sda partition (see log below). How can I recover my sda partition?

Sys log:

Aug 11 07:17:57 cimex kernel: [525773.116000] usb 2-2: new full speed USB device using uhci_hcd and address 6
Aug 11 07:17:57 cimex kernel: [525773.320000] usb 2-2: configuration #1 chosen from 1 choice
Aug 11 07:17:57 cimex kernel: [ 525773.320000] scsi16 : SCSI emulation for USB Mass Storage devices
Aug 11 07:18:02 cimex kernel: [525778.324000] scsi 16:0:0:0: Direct-Access     USB 2.0  (FS) FLASH DISK  1.00 PQ: 0 ANSI: 0 CCS
Aug 11 07:18:02 cimex kernel: [ 525778.328000] SCSI device sda: 511713 512-byte hdwr sectors (262 MB)
Aug 11 07:18:02 cimex kernel: [525778.332000] sda: Write Protect is off
Aug 11 07:18:02 cimex kernel: [525778.340000] SCSI device sda: 511713 512-byte hdwr sectors (262 MB)
Aug 11 07:18:02 cimex kernel: [525778.344000] sda: Write Protect is off
Aug 11 07:18:02 cimex kernel: [525778.344000]  sda: unknown partition table
Aug 11 07:18:02 cimex kernel: [525778.368000] sd 16:0:0:0: Attached scsi removable disk sda
Aug 11 07:18:02 cimex kernel: [525778.372000] sd 16:0:0:0: Attached scsi generic sg0 type 0

---

### Post by 5-HT on 2007-08-11
Ouch. It may just be the parition table. These might help:
[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

good luck!

---

### Post by cimex on 2007-08-11
Thank you,

I've tried TestDisk and Gparted, none of them detects /dev/sda. And I don't understand how I should add/recover/create it?

---

### Post by 5-HT on 2007-08-11
Sorry, not sure how to recover if those apps couldn't. Hopefully you had backups or the files weren't important? You can always repartition/reformat if needed. If the data was important, hopefully someone else can lend a hand.

---

### Post by cimex on 2007-08-11
I haven't lost any data, but I can't use the USB port as long as I don't have a /dev/sda?

---

