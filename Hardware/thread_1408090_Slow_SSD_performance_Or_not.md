---
title: "Slow SSD performance? Or not?"
date: 2010-02-15
forum: Hardware
---

### Post by antispin on 2010-02-15
I have just installed an Intel SSD X18-M G1 in my laptop (HP tx2-1244ca) and I'm a little surprised at the results I am getting from hdparm. The drive is rated for 250 MB/s read, 70 MB/s write out of the box.

I have implemented pretty much every tweak I can fix on the Internet (alignment, noatime, deadline, tmpfs etc...), plus a few I didn't expect (example: I need to run my CPU in "Performance" not "OnDemand" mode to get the best SSD performance).

A regular hdparm test shows poor read performance. Using O_DIRECT results in performance closer to what I was expecting. Can you tell me -- is my SSD performing at peak speed or not?

thanks!!!


```
sudo hdparm -FtT /dev/sda

/dev/sda:
 Timing cached reads:   1806 MB in  2.00 seconds = 902.91 MB/sec
 Timing buffered disk reads:  484 MB in  3.00 seconds = 161.14 MB/sec

/dev/sda:
 Timing O_DIRECT cached reads:   490 MB in  2.00 seconds = 244.91 MB/sec
 Timing O_DIRECT disk reads:  758 MB in  3.01 seconds = 252.18 MB/sec

```

```
sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       INTEL SSDSA1MH080G1GN                   
	Serial Number:      CVEM850100G2080IGN  
	Firmware Revision:  045C8820
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 1 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  156301488
	LBA48  user addressable sectors:  156301488
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	device size with M = 1024*1024:       76319 MBytes
	device size with M = 1000*1000:       80026 MBytes (80 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 31
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
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
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	    	Device-initiated interface power management
	   *	Software settings preservation
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 500151795907a169
	NAA		: 5
	IEEE OUI	: 001517
	Unique ID	: 95907a169
Checksum: correct

```

---

