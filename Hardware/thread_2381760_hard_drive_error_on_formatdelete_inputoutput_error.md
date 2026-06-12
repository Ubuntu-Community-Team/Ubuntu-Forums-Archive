---
title: "hard drive error on format/delete input/output error"
date: 2018-01-05
forum: Hardware
---

### Post by rgvet on 2018-01-05
Greetings - first time posting - linux/ubuntu novice

I have a Lenovo x120e which stopped working. It had W7 then W10 then it was halting forever. I tried the W10 partition and deleted even the special area reserved for recovery thus creating even a further havoc. Now I do no care I want it to be ububtu or lubuntu machine, There area sda and sdb. sdb is the main 300gb drive that is now inaccessible by either W10 partitioner (whic I do not care for anymore, as I wrote) nor by Ubuntu and Lubuntu USB. I cannot install Ubuntu/Lubuntu, I can only use the "try" from the USB. Non of the commands work with sdb. It always report input/output error. 

I just want to delete everyhting, format everything and have Lubuntu/Ubuntu on it.

The last try was this (I have su - it)

```
root@ubuntu:~# mkfs -t ntfs -F -Q -L "hello world" /dev/sdb
/dev/sdb is entire device, not just one partition.
mkntfs forced anyway.
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Error writing to /dev/sdb: Input/output error
Error writing non-resident attribute value.
add_attr_bitmap_positioned failed: Input/output error
Couldn't create $MFT: Input/output error

root@ubuntu:~# fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 7.5 GiB, 8054112256 bytes, 15730688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0e0e8e70

Device     Boot   Start     End Sectors  Size Id Type
/dev/sda1  *          0 2902111 2902112  1.4G  0 Empty
/dev/sda2       2888004 2892739    4736  2.3M ef EFI (FAT-12/16/32)


root@ubuntu:~# parted -l
Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? i                                                          
Model: Sandisk USB Ultra (scsi)
Disk /dev/sda: 32.2GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1479MB  1481MB  2425kB               EFI






Error: /dev/sdb: unrecognised disk label
Model: ATA WDC WD3200BEKT-0 (scsi)                                        
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
```


What shall I do?
(right now it is being "shred /dev/sdb")

---

### Post by sccman on 2018-01-05
Well, forgive me for asking, but what are you trying to accomplish? We need to know what the problem/goal is before we can give a solution. :D

---

### Post by rgvet on 2018-01-05
as I have written "I just want to delete everyhting, format everything and have Lubuntu/Ubuntu on it." I.e. use this as a Ubuntu/Lubuntu computer. I like his computer and it is a good machine and small - very handy. IT will be pretty much a Linux netbook like.

---

### Post by sccman on 2018-01-05
Oh okay I understand now.

By the look of things, it looks like the drive can be recognized and interacted with. There seems to be no hardware damage, which is a good thing.

Now the weird thing is why the computer can't recognize the partition table on sdb. Typically this should be gpt, msdos, or mbr for Windows. The partition table is essentially the "table of contents" for a drive that tells the computer about how the partitions are set up on the drive. When the computer boots up, it reads the partition table to know how the partitions are organized.

Typically if there is a problem with the partition table, it happens when there is an error from deleting or moving partitions around on a hard drive. It can also occur if a partition delete is aborted prematurely.

When the partition table is broken, the computer can't use the drive.

Depending on the severity of the damage, it's possible to fix the hard drive. There are a few possible solutions you could try to fix the partition table. Here is a website that explains them:

[https://www.interworks.com/blog/smatlock/2015/02/13/restore-damaged-or-corrupted-linux-partition-table](https://www.interworks.com/blog/smatlock/2015/02/13/restore-damaged-or-corrupted-linux-partition-table)

---

### Post by rgvet on 2018-01-05
sccman, you wrote: "Typically if there is a problem with the partition table, it happens when  there is an error from deleting or moving partitions around on a hard  drive. It can also occur if a partition delete is aborted prematurely." Well this is exactly what happened. I was trying to save it with W10 whence I moved partitions around; when the computer halted for very long I did interrupted it by 7sec pressing on the power button forcing it to shut down. Yes, I did all of these these things, multiple times. I was obviously wrong. I have learned my lesson. However, there was a problem before that for which I have started to meddle about with the partitions. I will go to the site and try..... finger crossed.
 Thank you - I shall be back.

---

### Post by sccman on 2018-01-05
Haha no worries it happened to me before too. That's how I know about it. I had to replace my hard drive in my laptop.

Let us know how it goes.

---

### Post by rgvet on 2018-01-05
It is this above that gives the problem. 
there is a constant error in the very beginning. general tests of both Ubuntu and W10 goes well. 
However all of them fail to read with and i/o. 
Even KillDisk.
If I take it out of the computer, will it help?
How can I reach as close as possible to ruling out hardware damage that is total loss?
KillDisk reports again and again "Cannot read sectors from..... (Error: 5)" - and it starts from 0.

---

### Post by sccman on 2018-01-05
You could try taking the hard drive out of the computer, but in my opinion I doubt it would fix the problem. The damage was at the software level, not the hardware level. If the hard drive was physically damaged it would make noises when it is running.

The only other problem I could think of at the hardware level would be the connectors themselves but like I said the damage was at the software level, not the hardware level.

You're welcome to try though.

Have you been able to use TestDisk?

---

### Post by rgvet on 2018-01-07
I have taken it out and purchase an adapter. Same situation - as you predicted.
I have tried variety of software, to no avail.
I will try test disk.

---

### Post by rgvet on 2018-01-07
I am having difficulties installing TestDisk on my ubuntu

---

### Post by rgvet on 2018-01-07
Oh, TestDisk is pretty similar to KillDisk. No success - TestDisk finds it (unlike gparted) but stuck forever on the Proceed.

---

### Post by rgvet on 2018-01-07
Sorry, no like TestDisk - but I have tried TestDisk

---

### Post by rgvet on 2018-01-07
Analyse - partition error.
Quick search - 
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sdb - 320 GB / 298 GiB - CHS 305245 64 32
Analyse cylinder  1075/305244: 00%
Read error at 1022/1/1 (lba=2093088)

---

### Post by rgvet on 2018-01-07
then-

Disk /dev/sdb - 320 GB / 298 GiB - CHS 305245 64 32


The harddisk (320 GB / 298 GiB) seems too small! (< 320 GB / 298 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...


The following partition can't be recovered:
     Partition               Start        End    Size in sectors
>  HPFS - NTFS          305243  63 32 305709  63 31     954368

---

### Post by rgvet on 2018-01-07
[ Continue ]
NTFS, blocksize=4096, 488 MB / 466 MiB

---

### Post by rgvet on 2018-01-07
Disk /dev/sdb - 320 GB / 298 GiB - CHS 305245 64 32


Warning: the current number of heads per cylinder is 64
but the correct value may be 128.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

---

### Post by rgvet on 2018-01-07
Then, what ever I do (including changing heads per cylinder to 128 as recommended), then write fails.

---

### Post by rgvet on 2018-01-07
even delete - 
Write error: Can't clear partition table.

---

### Post by rgvet on 2018-01-08
the problematic one is the 320GB (I think sdb)

grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ hdparm -I /dev/sda
/dev/sda: Permission denied
grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ sudo hdparm -I /dev/sda
[sudo] password for grps-ubuntu: 


/dev/sda:


ATA device, with non-removable media
	Model Number:       ST500LT012-1DG142                       
	Serial Number:      S3PLWZ7K
	Firmware Revision:  0002LVM1
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x0029) 
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		15	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  976773168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                  4096 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      476940 MBytes
	device size with M = 1000*1000:      500107 MBytes (500 GB)
	cache/buffer size  = unknown
	Form Factor: 2.5 inch
	Nominal Media Rotation Rate: 5400
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 254
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	Power-Up In Standby feature set
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	Idle-Unload when NCQ is active
	   *	READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	96min for SECURITY ERASE UNIT. 96min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000c500803c747e
	NAA		: 5
	IEEE OUI	: 000c50
	Unique ID	: 0803c747e
Checksum: correct
grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ sudo hdparm -I /dev/sdb


/dev/sdb:


ATA device, with non-removable media
	Model Number:       WDC WD3200BEKT-08PVMT1                  
	Serial Number:      WD-WX71A71D1701
	Firmware Revision:  02.01A02
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  625142448
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      305245 MBytes
	device size with M = 1000*1000:      320072 MBytes (320 GB)
	cache/buffer size  = 16384 KBytes
	Nominal Media Rotation Rate: 7200
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 0
	Advanced power management level: 128
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	Disable Data Transfer After Error Detection
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	Idle-Unload when NCQ is active
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Read/Write Long (AC1), obsolete
	   *	SCT Write Same (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
	    	unknown 206[14] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	58min for SECURITY ERASE UNIT. 58min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50014ee6017727fa
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 6017727fa
Checksum: correct
grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ sudo hdparm -g /dev/sdb


/dev/sdb:
 geometry      = 305245/64/32, sectors = 625142446, start = 0
grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ sudo hdparm -tT /dev/sdb


/dev/sdb:
read() failed: Input/output error
 Timing buffered disk reads: read() failed: Input/output error

---

### Post by rgvet on 2018-01-08
and again

grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ sudo hdparm -tT /dev/sdb


/dev/sdb:
read() failed: Input/output error
 Timing buffered disk reads: read() failed: Input/output error
grps-ubuntu@grpsubuntu-Lenovo-G50-70:~$ sudo hdparm -tT /dev/sdb


/dev/sdb:
read() failed: Input/output error
 Timing buffered disk reads: read() failed: Input/output error

---

### Post by rgvet on 2018-01-08
can hdparm help?

---

### Post by sccman on 2018-01-09
hdparm has to do with the power management and speed that the hard drive runs at. It doesn't have to deal with the data itself.

[https://wiki.archlinux.org/index.php/hdparm](https://wiki.archlinux.org/index.php/hdparm)

Try booting through a Live CD and run fdisk:

[https://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table](https://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table)

---

### Post by rgvet on 2018-01-10
I have tried again fdsik from live  - it was one of the very first tools I tried.
Well - I have given up. I assume that I can give it to a professional, however it can be replaced with a couple dozens of bucks so I will do just that. There is no info of any importance on it. I do think it is a hardware error somewhere along sector 0. All my fault fiddling with it to the bitter end. Thanks SCCMAN. It was a pleasure and I have learned about this thing for the first time. Alla prossima

---

