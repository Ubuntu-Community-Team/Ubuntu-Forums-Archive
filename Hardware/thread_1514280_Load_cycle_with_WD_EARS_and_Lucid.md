---
title: "Load_cycle with WD EARS and Lucid"
date: 2010-06-20
forum: Hardware
---

### Post by rj45 on 2010-06-20
Hi all,

Apoligies if this matter is considered solved, but I've got 2 WD EARS drives, running Lucid, (desktop machine) and my load_cycle count is incrementing about every 15 seconds.

I've read and applied everything I found, but no joy.

I set "hdparm -B 254", and checked for laptop_mode, and other tips.
Checked my BIOS settings there, power management is disabled.

Is there anyway I can find what keeps parking my heads?

TIA,
-don

---

### Post by rj45 on 2010-06-22
here's the output of "hdparm -I /dev/sda".
Everything looks good to me.....

[email]root@goober:~/.Virtua[/email]lBox/Machines# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD15EARS-00Z5B1                     
	Serial Number:      WD-WMAVU1476657
	Firmware Revision:  80.00A80
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
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
	LBA48  user addressable sectors: 2930277168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:     1430799 MBytes
	device size with M = 1000*1000:     1500301 MBytes (1500 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 128, current value: 254
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
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	342min for SECURITY ERASE UNIT. 342min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee001e93a14
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 001e93a14
Checksum: correct

---

