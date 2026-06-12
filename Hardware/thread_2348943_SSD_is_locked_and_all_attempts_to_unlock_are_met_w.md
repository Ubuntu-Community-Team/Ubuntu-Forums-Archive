---
title: "SSD is locked and all attempts to unlock are met with I/O errors."
date: 2017-01-09
forum: Hardware
---

### Post by radish888 on 2017-01-09
It's not showing up in fdisk, so here's my hdparm -I:

```


/dev/sda:


ATA device, with non-removable media
	Model Number:       M4-CT128M4SSD2                          
	Serial Number:      
	Firmware Revision:  
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x0028) 
	Supported: 9 8 7 6 5 
	Likely used: 9
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  250069680
	LBA48  user addressable sectors:  250069680
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      122104 MBytes
	device size with M = 1000*1000:      128035 MBytes (128 GB)
	cache/buffer size  = unknown
	Form Factor: 2.5 inch
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	    	SMART feature set
	   *	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
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
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Write Same (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	   *	Data Set Management TRIM supported (limit 8 blocks)
	   *	Deterministic read data after TRIM
Security: 
	Master password revision code = 65534
		supported
		enabled
		locked
	not	frozen
		expired: security count
		supported: enhanced erase
	Security level high
	2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 500a07510902b401
	NAA		: 5
	IEEE OUI	: 00a075
	Unique ID	: 10902b401
Checksum: correct



```

I keep trying to unlock it, but everytime I am met with a I/O error:

```
hdparm --user-master m --security-unlock EINS /dev/sda security_password: "EINS"


/dev/sda:
 Issuing SECURITY_UNLOCK command, password="EINS", user=master
SECURITY_UNLOCK: Input/output error



```


What do I do? Is there a special master password for crucial ssds?

---

### Post by QIII on 2017-01-09
I don't think you want 

```
security_password: "foo"
```

in the command.  I think that is output as I recall.

---

### Post by efflandt on 2017-01-09
Look through your .bash_history and see how you locked it up in the first place.
Have you tried:```
sudo hdparm --user-master m --security-unlock EINS /dev/sda
sudo hdparm --user-master m --security-disable Eins /dev/sda
```Not sure what the difference is between --user-master m (or u).

---

