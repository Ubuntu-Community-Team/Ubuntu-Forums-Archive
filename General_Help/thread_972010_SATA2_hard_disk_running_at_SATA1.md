---
title: "SATA2 hard disk running at SATA1"
date: 2008-11-05
forum: General Help
---

### Post by xak on 2008-11-05
My Lenovo T61p has a Seagate ST9160823AS drive, which [supports SATA2 3.0Gbps]("http://www.seagate.com/www/en-us/products/laptops/momentus/momentus_7200.2/") transfer rate, as does the [ICH8M chipset]("http://www.intel.com/Products/Notebook/Chipsets/GM965/GM965-technicaldocuments.htm").  However, my Intrepid installation is not detecting it as such (see dmesg output below).  I have also tried removing the jumper installed by default on the drive, but this made no change.  Any ideas?  Let me know if I can provide any more info.

```
$ lspci |grep SATA
00:1f.2 SATA controller: [COLOR="Red"]Intel Corporation 82801HBM/HEM[/COLOR] (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
```

```
$ dmesg |grep SATA
[    3.325176] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATA mode
[    3.325727] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 2297
[    3.325734] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 2297
[    3.644085] ata1: [COLOR="Red"]SATA link up 1.5 Gbps[/COLOR] (SStatus 113 SControl 300)
[    3.980086] ata3: SATA link down (SStatus 0 SControl 300)
```

```
# hdparm -I /dev/sda
/dev/sda:

ATA device, with non-removable media
	Model Number:       ST9160823AS                             
	Serial Number:      <removed>
	Firmware Revision:  3.CME   
Standards:
	Supported: 7 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  312581808
	device size with M = 1024*1024:      152627 MBytes
	device size with M = 1000*1000:      160041 MBytes (160 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
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
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	Disable Data Transfer After Error Detection
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	SATA-I signaling speed (1.5Gb/s)
[COLOR="Red"]	   *	SATA-II signaling speed (3.0Gb/s)[/COLOR]
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	56min for SECURITY ERASE UNIT. 56min for ENHANCED SECURITY ERASE UNIT.
Checksum: correct
```

Thanks! ):P

---

### Post by xak on 2008-11-06
This is not my first post asking for help with a strange issue with lots of listed detail and background information that hasn't gotten any replies on these forums.  What is the reason for this?  I have tried to supply all possible related information so that others could share their knowledge and help me find a solution.  Have I not supplied enough?  Is the issue just too complex?  Is it just that nobody cares or that nobody has this same issue?

Thanks for any input.

---

### Post by michaelandrews on 2009-04-10
The ICH8M chipset supports SATA II but is not SATA II natively.  This means that you can plug a SATA II drive in but it will operate at SATA I speeds (up to 1.5 Gbps).

---

### Post by pbpersson on 2009-04-10
> **xak said:**
>   Have I not supplied enough?  Is the issue just too complex?  Is it just that nobody cares or that nobody has this same issue?


Sometimes getting no response is better than getting misleading information from well intentioned people, forcing you to spend weeks chasing down leads that turn out to be dead ends.

1.  You have already done all the research and have collected data
2.  Your problem is way over my head

I was going to say remove the jumper but when you said you had already done this, I had run out of suggestions.

---

