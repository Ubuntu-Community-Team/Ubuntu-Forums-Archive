---
title: "SSD Disk does not have a valid partition table"
date: 2015-04-20
forum: Hardware
---

### Post by nganon2 on 2015-04-20
Hello,

My two year old 160 GB Intel SSD has failed.
BIOS detects the disk but cannot boot. I am guessing the partition table is lost. 

I booted from live ubuntu on flash disk and here is the relavent [B]dmesg output:
[/B]
[    8.322940] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.323839] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    8.323845] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    8.324430] ata1.00: HPA detected: current 16384, native 312581808
**[    8.324682] ata1.00: ATA-8: INTEL SSDSA2BW160G3L, 4PC1LE04, max UDMA/133**
[    8.324939] ata1.00: 16384 sectors, multi 16: LBA48 
[    8.325573] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    8.325578] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    8.326164] ata1.00: configured for UDMA/133
[    8.326495] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2BW16 4PC1 PQ: 0 ANSI: 5
**[    8.327040] sd 0:0:0:0: [sda] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)**
[    8.327056] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.327989] usb 1-1.3: New USB device found, idVendor=147e, idProduct=2016
[    8.327991] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    8.327993] usb 1-1.3: Product: Biometric Coprocessor
[    8.327995] usb 1-1.3: Manufacturer: UPEK
[    8.335580] sd 0:0:0:0: [sda] Write Protect is off
[    8.336017] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.336039] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.337515]  sda: unknown partition table
[    8.338051] sd 0:0:0:0: [sda] Attached SCSI disk


fdisk cannot recognize the partition table.

**# fdisk -l /dev/sda**

Disk /dev/sda: 8 MB, 8388608 bytes
255 heads, 63 sectors/track, 1 cylinders, total 16384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/sda doesn't contain a valid partition table**


gpart guesses a partition table with no size and block numbers. 
As far as I can remember, there two physical and two logical partitions. 
So gpart's prediction is correct but I am clueles about sizes.

**# gpart /dev/sda **

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


I was positive that testdisk could find a similar table with sizes and I can write a new mbr but it didn't

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sda - 8388 KB / 8192 KiB - INTEL SSDSA2BW160G3L
     CHS 1 255 63 - sector size=512

>[ Analyse  ] Analyse current partition structure and search for lost partitions
 [ Advanced ] Filesystem Utils
 [ Geometry ] Change disk geometry
 [ Options  ] Modify options
 [ MBR Code ] Write TestDisk MBR code to first sector
 [ Delete   ] Delete all data in the partition table
 [ Quit     ] Return to disk selection


Disk /dev/sda - 8388 KB / 8192 KiB - CHS 1 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors


**Partition sector doesn't have the endmark 0xAA55**

>[Quick Search]

Disk /dev/sda - 8388 KB / 8192 KiB - CHS 1 255 63
     Partition               Start        End    Size in sectors


**No partition found or selected for recovery**


 >[Deeper Search]

Disk /dev/sda - 8388 KB / 8192 KiB - CHS 1 255 63

     Partition                  Start        End    Size in sectors

**No partition found or selected for recovery**



So to sum up, there are four paritions in the disk with no partition table recognized with the following errors:

[    8.327040] sd 0:0:0:0: [sda] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)

Disk /dev/sda doesn't contain a valid partition table

Partition sector doesn't have the endmark 0xAA55

No partition found or selected for recovery

What else can I try to recover the partition table. 

Or can you tell whether the actual problem is the partition table. 

Thanks very much for sharing your opinions in advance!

---

### Post by oldfred on 2015-04-20
Part of reason I prefer gpt over MBR(msdos) partitioning, it has a backup partition table and more error checking.

I see this and that is saying drive is just not seen correctly, which is not just partition table. Your 160GB drive is found as 8MiB drive?
**[    8.327040] sd 0:0:0:0: [sda] 16384 512-byte logical blocks: (8.38 MB/8.00 MiB)**

I do not think any Linux tools then can fix that, unless there is some lower level tools. I might check with Vendor and see what low level repair tools/drive checkers they may have.

---

### Post by nganon2 on 2015-04-20
Thanks for the hint.

Apparently it is a firmware bug and Intel has released an update for that. 

For anyone's future reference. there no apparent way for data recovery but the drive itself can be rescued.

[https://communities.intel.com/thread/24205](https://communities.intel.com/thread/24205)
[http://askubuntu.com/questions/409684/image-or-reset-broken-ssd](http://askubuntu.com/questions/409684/image-or-reset-broken-ssd)

---

### Post by weatherman2 on 2015-04-20
Thanks for the heads-up!  I have one of those 320's in a server that has been humming along for 2+ years.  I just checked the firmware and it was updated to what Intel claims was the latest in your link from 2011.  So I guess I'm safe!

---

