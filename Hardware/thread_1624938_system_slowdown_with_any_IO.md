---
title: "system slowdown with any IO"
date: 2010-11-18
forum: Hardware
---

### Post by weblordpepe on 2010-11-18
Hi there guys.

I've had an issue with my Ubuntu system since version 7 or so and I have not been able to track it down with each Ubuntu dist upgrade I have done over time.

The system slows to a creeping halt on any IO, usually disk activity, and I can't figure out why. I have determined it's not just my hard drive (SATA/nvidia chipset) because writing to a USB flash drive also causes the slowdown.

IOwait goes through the roof, but as to my understanding high IOwait basically means the disk is the bottleneck and thats acceptable most of the time.

Now there's no speed issue with the drives my hard drives are fast as bolts: Even hdparm shows it:
```
/dev/sda:
 Timing cached reads:   1294 MB in  2.00 seconds = 647.06 MB/sec
 Timing buffered disk reads:  208 MB in  3.10 seconds =  67.18 MB/sec
```

Now, interestingly when doing these tests the system slows down (including mouse cursor, any audio playing or videos) when doing these tests. It completely stops momentarily while doing the second test (the straight disk read)

My Ubuntu version is 9.10, and my chipset is nForce4 (uses sata_nv for disk access, but like I said this happens on flash too).

* I have tried turning off swap. This only helps as much as the writes/reads to swap aren't happening.. but the issue still remains. Swappiness is now on 3 for what its worth.

* I have tried using different io schedulers (noop, etc) on my hard drive with no difference.

** With the little effect of schedulers + it being on multiple unrelated drives I suspect its not related to my drives.. but the only troubleshooting tools I know are for hard drives.

Questions:
* What else can I do to narrow down the issue?
* What, if anything, changed during the switch from 6.10 to 7.04 related to io?

* What tools can I use? Please halp.. this is terrible. For so long I have had stuttering on my VLC when I hit play when the file is loaded into RAM.

Here is my Disk controller as listedin lspci:
```

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Albatron Corp. Device 3404
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at cc00 [size=16]
	Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: sata_nv
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Albatron Corp. Device 3404
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at b800 [size=16]
	Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: sata_nv

```

And here's my hard drive info (from hdparm) for what its worth:

```
/dev/sda:

ATA device, with non-removable media
	Model Number:       ST31000340AS                            
	Serial Number:      9QJ0TPES
	Firmware Revision:  SD15    
	Transport:          Serial
Standards:
	Used: unknown (minor revision code 0x0029) 
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
	LBA48  user addressable sectors: 1953525168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1000*1000:     1000204 MBytes (1000 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: 7200
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
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
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	202min for SECURITY ERASE UNIT. 202min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c5000cd43ee0
	NAA		: 5
	IEEE OUI	: 000c50
	Unique ID	: 00cd43ee0
Checksum: correct

```

Ubuntu 9.10:
Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010

AMD Athlon 64: 2ghz
1GB dual channel ram
1TB seagate barracuda.

---

### Post by weblordpepe on 2010-11-19
Amazingly, the one night I decide to seriously look at the problem, the world decides to go bananas and the issue is front page news on slashdot & everywhere else. This issue was solved by using the config [here]("http://lxer.com/module/newswire/ext_link.php?rid=144793")

It is a userspace implementation of a patch which will be coming into the next kernel release (2.6.37 i think).

Its awesome. Its like having my computer back.

---

### Post by kwgivler on 2011-09-14
This is in the kernel now (2.6.38) right? I'm still having problems with IOWait being through the roof. I didn't have problems in gentoo.

---

