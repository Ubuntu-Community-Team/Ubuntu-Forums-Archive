---
title: "Ubuntu support for Toshiba Gigastick 4 GB"
date: 2010-10-31
forum: Hardware
---

### Post by samuele.pretini on 2010-10-31
Hi at all,

when I try to insert my new Toshiba Gigastick usb driver I obtain this message from kernel log:

--------------------------------

kernel: [  183.704090] usb 1-1: new high speed USB device using ehci_hcd and address 3
kernel: [  183.840598] usb 1-1: configuration #1 chosen from 1 choice
kernel: [  183.842377] scsi7 : SCSI emulation for USB Mass Storage devices
kernel: [  183.842652] usb-storage: device found at 3
Oct 31 13:57:15 samuele76-Altran kernel: [  183.842661] usb-storage: waiting for device to settle before scanning
kernel: [  188.840369] usb-storage: device scan complete
kernel: [  188.841311] scsi 7:0:0:0: Direct-Access              TOSHIBA USB HDD  PMAP PQ: 0 ANSI: 0 CCS
kernel: [  188.842788] sd 7:0:0:0: Attached scsi generic sg2 type 0
kernel: [  191.915162] sd 7:0:0:0: [sdb] Attached SCSI removable disk
kernel: [  191.925183] sd 7:0:0:0: [sdb] 7862396 512-byte logical blocks: (4.02 GB/3.74 GiB)
kernel: [  191.925789] sd 7:0:0:0: [sdb] Assuming drive cache: write through
kernel: [  191.928072] sd 7:0:0:0: [sdb] Assuming drive cache: write through
kernel: [  191.928081]  sdb:
kernel: [  200.442936] sd 7:0:0:0: [sdb] Unhandled sense code
kernel: [  200.442949] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [  200.442960] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
kernel: [  200.442972] sd 7:0:0:0: [sdb] Add. Sense: Unrecovered read error
kernel: [  200.442984] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
kernel: [  200.443007] end_request: I/O error, dev sdb, sector 0
kernel: [  200.443020] Buffer I/O error on device sdb, logical block 0
kernel: [  200.443030] Buffer I/O error on device sdb, logical block 1
kernel: [  200.485478] ldm_validate_partition_table(): Disk read failed.
kernel: [  200.485503] Dev sdb: unable to read RDB block 0
kernel: [  200.503575]  unable to read partition table

--------------------------------

And then I can not access to usb drive.

When also I start my virtual machine with Windows XP, I can use the drive inside XP, but when I shut down virtual machine, I can use the usb drive also in Ubuntu.

If I disconnect the usb drive and re-connect, ubuntu don't mount it, with the kernel log attached.

Can someone of us to explain me this strange behaviour?
And how can I use the usb drive with Ubuntu.

My distribuition is: 10.4, my kernel is: 2.6.32-25

Thanks a lot.

Samuele

---

