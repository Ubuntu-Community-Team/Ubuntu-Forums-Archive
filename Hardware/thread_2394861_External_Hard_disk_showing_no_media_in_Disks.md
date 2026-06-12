---
title: "External Hard disk showing no media in Disks"
date: 2018-06-22
forum: Hardware
---

### Post by sachingulati on 2018-06-22
Hi, 
I removed my external hard disk (Seagate) directly from a windows system and now it is not working anymore.
I'm trying to fix it via ubuntu now, and when I try to check it in Disks (gnome utility), it says no media. 
I have important data in this disk and want to recover all data as well. 

I have tried to gather as much input as I can, by running some commands that I could find online in help forums. 



**sudo ****lshw**** -c disk**


*-disk
description: SCSI Disk
product: JMS579
vendor: JMICRON
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sdb
configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512


**sudo ****lshw**[B] -class disk -class storage
[/B]
*-usb:1
description: Mass storage device
product: USB Mass Storage
vendor: JMicron
physical id: 4
bus info: usb@2:4
logical name: scsi4
version: 1.00
serial: 152D00579000
capabilities: usb-2.10 scsi emulated scsi-host
configuration: driver=usb-storage maxpower=34mA speed=480Mbit/s
*-disk
description: SCSI Disk
product: JMS579
vendor: JMICRON
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sdb
configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512




**sudo hdparm -I /dev/sdb**


/dev/sdb:
SG_IO: bad/missing sense data, sb[]: 70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


ATA device, with non-removable media
Standards:
Likely used: 1
Configuration:
Logical max current
cylinders 0 0
heads 0 0
sectors/track 0 0
--
Logical/Physical Sector size: 512 bytes
device size with M = 1024*1024: 0 MBytes
device size with M = 1000*1000: 0 MBytes 
cache/buffer size = unknown
Capabilities:
IORDY not likely
Cannot perform double-word IO
R/W multiple sector transfer: not supported
DMA: not supported
PIO: pio0 
    
[B]sudo smartctl -a -d scsi /dev/sdb

[/B]
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-127-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF INFORMATION SECTION ===
Vendor: JMICRON
Product: JMS579
Compliance: SPC-4
Device type: disk
Local Time is: Fri Jun 22 23:07:23 2018 IST
device Test Unit Ready [unsupported scsi opcode]
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.


**fdisk**[B] -l

[/B]Fdisk doesn't show any result for this disk. as it is not mounted anywhere. 


Any help is highly appreciated, thanks in advance.

---

### Post by oldfred on 2018-06-22
Did you partition in Windows or just write data to it as a large floppy drive?
It needs partitions formatted NTFS.

Then if just unplugged from Windows without unmounting it may be corrupted and need chkdsk.
Or Windows fast start up may have left it in hibernated state and Linux NTFS driver will not mount it read/write. If that you may be able to force read only mode.

What does Windows show?

---

### Post by sachingulati on 2018-06-22
this drive was always being used in Windows 8 and 10 with partition. I'm not sure about the previous file system, as this disk belongs to my friend, who isn't that techy to know all these things. 


[COLOR=#000000]> Then if just unplugged from Windows without unmounting it may be corrupted and need chkdsk.[/COLOR]
I'm assuming this was the case as it stopped working after that. Windows system doesn't show this disk at all. I can see this disk in the devices connected through usb but nothing more. 

this is the output from **sudo**[B] dmesg:
[/B]
[141307.332889] usb 2-4: USB disconnect, device number 5
[141310.499914] usb 2-4: new high-speed USB device number 7 using xhci_hcd
[141310.628540] usb 2-4: New USB device found, idVendor=152d, idProduct=0579
[141310.628544] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[141310.628547] usb 2-4: Product: USB Mass Storage
[141310.628549] usb 2-4: Manufacturer: JMicron
[141310.628551] usb 2-4: SerialNumber: 152D00579000
[141310.629107] usb-storage 2-4:1.0: USB Mass Storage device detected
[141310.629201] scsi host4: usb-storage 2-4:1.0
[141311.628514] scsi 4:0:0:0: Direct-Access     JMICRON  JMS579                PQ: 0 ANSI: 6
[141311.629170] sd 4:0:0:0: Attached scsi generic sg2 type 0
[141311.629942] sd 4:0:0:0: [sdb] Unit Not Ready
[141311.629953] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[141311.629960] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
[141311.632053] sd 4:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[141311.632064] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[141311.632072] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
[141311.632253] sd 4:0:0:0: [sdb] Write Protect is off
[141311.632261] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[141311.632435] sd 4:0:0:0: [sdb] Asking for cache data failed
[141311.632441] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[141311.635917] sd 4:0:0:0: [sdb] Unit Not Ready
[141311.635927] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[141311.635935] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
[141311.639186] sd 4:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[141311.639197] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[141311.639205] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
[141311.639534] sd 4:0:0:0: [sdb] Attached SCSI disk
[141594.937486] EXT4-fs (sdb): unable to read superblock
[141594.937770] EXT4-fs (sdb): unable to read superblock
[141594.938048] EXT4-fs (sdb): unable to read superblock
[141594.938335] SQUASHFS error: squashfs_read_data failed to read block 0x0
[141594.938337] squashfs: SQUASHFS error: unable to read squashfs_super_blockthis one says ext4 file system but I don't think that works with windows system without making adjustments.

---

### Post by oldfred on 2018-06-22
Some large external drives had unique partitioning to work with XP as XP could not support drives over 2TiB as that was the MBR(msdos) partitioning limit. 

But best to try to repair from Windows first since NTFS drive.

---

### Post by Autodave on 2018-06-23
Try this: ,ake sure your machine is updated!  I just came back from vacation. Every night I would try to d-l my pics off of the SD card to may laptop. Sometimes the SD card was recognized, sometimes not. When It was recognized, I could copy maybe one or two pics from it before I lost connection with it. Removing and reinstalling it sometimes worked for another pic or two, sometimes it wouldn't recognize it. I tried 4 different USB ports to no avail.  Upon getting home today, I still had the same problem. However, the message came up that there were updates available (and I had updated 2 nights ago). Upon doing the updates, it works perfectly now.

---

