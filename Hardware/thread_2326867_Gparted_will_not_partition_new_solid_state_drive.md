---
title: "Gparted will not partition new solid state drive"
date: 2016-06-05
forum: Hardware
---

### Post by raymondvillain on 2016-06-05
Ubuntu 14.04, new Sandisk 120 Gbyte ssd.  If I boot to windows the drive doesn't even show up.

Open Gparted in Ubuntu, select /dev/sdd, of course "partition" and "File system" columns show "unallocated".  Right click on the relevant line, information: "Warning: /dev/sdd: unrecognized disk label".

Tried to get Gparted to create a partition table but nothing happens.  In a terminal window, run "sudo fdisk -l -u /dev/sdd, output follows:

> ~$ sudo fdisk -l -u /dev/sdd

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdd doesn't contain a valid partition table

Also in terminal output of command "sudo hdparm -I /dev/sdd":

> ~$ sudo hdparm -I /dev/sdd

/dev/sdd:

ATA device, with non-removable media
	Model Number:       SanDisk SDSSDA120G                      
	Serial Number:      161956405770        
	Firmware Revision:  Z22000RL
	Media Serial Num:   
	Media Manufacturer: 
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x0110) 
	Supported: 9 8 7 6 5 
	Likely used: 9
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  234441648
	LBA48  user addressable sectors:  234441648
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      114473 MBytes
	device size with M = 1000*1000:      120034 MBytes (120 GB)
	cache/buffer size  = unknown
	Form Factor: 1.8 inch
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 1
	Advanced power management level: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	    	Look-ahead
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
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	    	Device Sleep (DEVSLP)
	   *	Data Set Management TRIM supported (limit 8 blocks)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5001b444a4be8e56
	NAA		: 5
	IEEE OUI	: 001b44
	Unique ID	: 4a4be8e56
Checksum: correct
Device Sleep:
	DEVSLP Exit Timeout (DETO): 70 ms (drive)
	Minimum DEVSLP Assertion Time (MDAT): 31 ms (drive)

Can one format an SSD drive from the command line?  Want to use it for Ubuntu Studio.  Any suggestions greatly appreciated.

---

### Post by raymondvillain on 2016-06-05
Solved, sort of.  Booted to windows, used "manage" on file explorer, initialized partition (GPT type), then re-booted to Ubuntu and Gparted could see the drive and do its thing.  But running hdparm in a terminal window still returns "frozen".

---

### Post by oldfred on 2016-06-05
You only use fdisk for MBR(msdos) partitioned drives. Although now there is a new fdisk in 16.04 that does support gpt.
You use parted or gdisk for gpt partitioned drives. But I always have used gparted and selected gpt under device before anything else.

 Use hdparm to unfreeze
[http://ubuntuforums.org/showthread.php?t=2317805](http://ubuntuforums.org/showthread.php?t=2317805)
Info on freeze
[https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

---

### Post by gedakc on 2016-06-06
The issue was that the SSD drive did not yet have a partition table and hence no new partitions could be created.

In GParted you can create a partition table using the **Device -> Create Partition Table** menu option.  Many different partition table types are supported such as msdos/mbr and gpt.  See [GParted Manual - Creating a New Partition Table]("http://gparted.org/display-doc.php?name=help-manual#gparted-create-partition-table").

Several clues to the issue were provided by the partitioning tools used such as the following text messages:

gparted - *Warning: /dev/sdd: unrecognized disk label*
fdisk - *Disk /dev/sdd doesn't contain a valid partition table*

A disk label is a term synonymous with partition table.

---

### Post by yoshii on 2016-06-07
> **gedakc said:**
> 
A disk label is a term synonymous with partition table.

Yeah, actually that's not true at all.  
A partition table is a partition table.  
A disk/volume label is a disk/volume label.  
They are not the same.  

I believe a partition table can contain the structure of a disk/volume, including possibly many different (optional) labels for many different partitions.  
The lable is just the friendly name that the user gives to the disk/volume, such as "George" or "PNY" or "TOSHIBA" or "MyFlashDrive".  

The partition table has data about how many partitions there are, what sizes they are, the gaps between them, and the conditional flags.  

The other possible difference is that the physical disk lable might mean the hardware manufacturer's model name of the drive, such as...

[h=1]WD3200JS[/h]...for a Western Digital (brand) 320 GB 7200 rpm internal SATA hard drive.  

This information is stored somewhere near or around or maybe in the partition table (perhaps), or maybe it's in the firmware of the drive.  I forget to be honest, but it's not the same as the volume label which you can choose manually in gParted or whatnot.

---

