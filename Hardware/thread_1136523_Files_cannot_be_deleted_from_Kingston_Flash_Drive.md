---
title: "Files cannot be deleted from Kingston Flash Drive"
date: 2009-04-25
forum: Hardware
---

### Post by binukavumkal on 2009-04-25
Hi All, 
I am not able to delete the files in the Kingston flash drive. I have root privileges. still it is not showing delete option and nothing happens when try to press Del Buttion

I am ok to clean up the flash drive. Is there any way?

Thanks in Advance

---

### Post by binukavumkal on 2009-04-25
It is mounted as read only, I found out. How can we mount it read write mode?

---

### Post by murderslastcrow on 2009-04-25
Is there a switch on that drive somewhere to "unlock" it? Many drives from this manufacturer have them. An easy shortcut (if you don't have too many important files on it) is to format the flash drive.

---

### Post by binukavumkal on 2009-04-26
Following is the message from dmesg

[ 1447.600601] usb 4-5: new high speed USB device using ehci_hcd and address 3
[ 1447.743053] usb 4-5: configuration #1 chosen from 1 choice
[ 1447.897868] usbcore: registered new interface driver libusual
[ 1447.960348] Initializing USB Mass Storage driver...
[ 1447.975899] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1447.979434] usbcore: registered new interface driver usb-storage
[ 1447.979451] USB Mass Storage support registered.
[ 1447.980236] usb-storage: device found at 3
[ 1447.980241] usb-storage: waiting for device to settle before scanning
[ 1452.980767] usb-storage: device scan complete
[ 1452.982058] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1453.224910] sd 2:0:0:0: [sdb] 15646720 512-byte hardware sectors (8011 MB)
[ 1453.226049] sd 2:0:0:0: [sdb] Write Protect is off
[ 1453.226059] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1453.226063] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1453.229905] sd 2:0:0:0: [sdb] 15646720 512-byte hardware sectors (8011 MB)
[ 1453.230778] sd 2:0:0:0: [sdb] Write Protect is off
[ 1453.230786] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1453.230790] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1453.230803]  sdb: sdb1
[ 1453.232074] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1453.232149] sd 2:0:0:0: Attached scsi generic sg2 type 0

---

### Post by binukavumkal on 2009-04-26
When I explore the USB drive to see the files, i get the following message

[ 1576.199743] FAT: Filesystem panic (dev sdb1)
[ 1576.199758]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1576.199762]     File system has been set read-only

---

### Post by binukavumkal on 2009-04-26
The following command ( after a search in Google) solved the issue

sudo dosfsck -a /dev/sdb1

Then safely removed the USB drive.

Plugged in again. It worked.

Thanks a lot

---

### Post by nhat on 2009-04-26
Just have the command directed to the drive right? Like /media/disk-1?

---

### Post by PaulHuffman on 2011-08-22
I've got two 4GB SDHC cards that are stubbornly read-only.  After a Picasa Import with delete imported files, it leaves the photos on the cards with a little red x in a circle on the photos Picasa can't delete.  The cards just get fuller and fuller.  Only my camera can delete them, but that's either delete everything or awkwardly delete one at a time.  

I tried sudo dosfsck -a /dev/sdb1 but got 
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
open: Read-only file system

On Windows, chkdsk said it was unavailable for a RAW file system.

Yes, the read protect sliding tape is set away from "protect".  Tried this slider both ways.

---

