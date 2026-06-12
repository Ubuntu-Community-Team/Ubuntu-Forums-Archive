---
title: "USB hard drive : used to work fine, now isn't recognized?"
date: 2010-02-10
forum: Hardware
---

### Post by Fillanzea on 2010-02-10
My USB drive used to work on my computer (HP Mini running Ubuntu 9.04) without a problem. Lately it isn't recognized. I upgraded to 9.10, but I'm not sure whether that's connected to the change or not. 

I was able to find several tutorials on mounting USB drives -- and yes, I admit to being terribly inexperienced at using the terminal; but the results of the commands I'm typing in don't seem to be anything at all like how they should be turning out. This is as much as I can figure out by myself; any help beyond here would be appreciated.

I have another computer that has Mac OS 10.6 installed on it, and that computer isn't recognizing the drive either. 

**EDIT: **I rebooted and this time it mounted automatically, but I get a "permission denied" message when trying to save anything. Tried chmod and it still isn't letting me do it. 

emily@emily-laptop:~$ ls -l /dev/sdb
brwxrwxrwx 1 root disk 8, 16 2010-02-10 12:03 /dev/sdb

I'm leaving the information I added earlier up in case there's something odd going on there.

emily@emily-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Sienna]Bus 001 Device 003: ID 0917:0524 SmartDisk Corp. [/COLOR]
Bus 001 Device 002: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(SmartDisk Corp. is the company that made the drive)

emily@emily-laptop:~/Desktop$ tail /var/log/messages
Feb 10 11:31:27 emily-laptop kernel: [66968.100122] usb 1-1: new high speed USB device using ehci_hcd and address 4
Feb 10 11:31:28 emily-laptop kernel: [66968.257627] usb 1-1: configuration #1 chosen from 1 choice
Feb 10 11:31:28 emily-laptop kernel: [66968.261850] scsi3 : SCSI emulation for USB Mass Storage devices

emily@emily-laptop:~/Desktop$ dmesg | grep -i "SCSI"
[    0.467105] SCSI subsystem initialized
[    1.324277] scsi0 : ata_piix
[    1.324479] scsi1 : ata_piix
[    1.481736] scsi 0:0:0:0: Direct-Access     ATA      SanDisk pSSD 16G SSD  PQ: 0 ANSI: 5
[    1.482068] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.485665] sd 0:0:0:0: [sda] Attached SCSI disk
[50485.132270] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[52368.833263] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[66261.842228] scsi2 : SCSI emulation for USB Mass Storage devices
[66266.851282] scsi 2:0:0:0: Direct-Access     FUJITSU  MHV2060AH        0000 PQ: 0 ANSI: 0
[66266.852988] sd 2:0:0:0: Attached scsi generic sg1 type 0
[66266.975909] sd 2:0:0:0: [sdb] Attached SCSI disk
[66968.261850] scsi3 : SCSI emulation for USB Mass Storage devices
[66973.264809] scsi 3:0:0:0: Direct-Access     FUJITSU  MHV2060AH        0000 PQ: 0 ANSI: 0
[66973.267703] sd 3:0:0:0: Attached scsi generic sg1 type 0
[66973.692156] sd 3:0:0:0: [sdb] Attached SCSI disk

emily@emily-laptop:~/Desktop$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SanDisk pSSD 16G Rev: SSD 
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: FUJITSU  Model: MHV2060AH        Rev: 0000
  Type:   Direct-Access                    ANSI  SCSI revision: 00
emily@emily-laptop:~/Desktop$ lsmod | grep -i usb
usb_storage            52576  0

I thought I made some progress and  I got: 
emily@emily-laptop:~/Desktop$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
64 heads, 32 sectors/track, 57231 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

