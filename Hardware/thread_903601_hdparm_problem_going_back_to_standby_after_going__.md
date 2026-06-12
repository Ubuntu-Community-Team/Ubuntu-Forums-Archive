---
title: "hdparm: problem going back to standby after going  to active"
date: 2008-08-28
forum: Hardware
---

### Post by lstepnio on 2008-08-28
I have JBOD array setup with mixed SATA drives. The system has hdparm configured to standby the JBOD drives without much hassles but one of my drives is having an odd issue. The drive in question when it wakes from a timed idle standby the drive will not go back into idle standby without having to again issue hdparm -S XX /dev/sdXX command.

The issue here is certainly not disk activity as verified by /proc/diskstats, unmounting the drive, lsof, lm_profiler. Once the drive going to standby it does go active unless there is specific user activity. I've attempted looking into laptop mode hooks, and various other packages which attempt to handle the spin down of hard drives which much of the same result. I have disabled and enabled SMART on the drive, checked possible jumpers on the drive, system BIOS along with SATA ports the other drives are working with perfectly. The same drive seems to have no issue going in and out of standby under XP when attached to my other machine.

The best work-around I have in mind short of any suggestions someone might have here is a script to check /proc/diskstats along with hddparm -C /dev/sdXX and issue the hddparm -S XX or -y as needed. This seems ugly and I'm hoping I'm simply missing something simple.

```

hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       SAMSUNG HD103UJ                         
	Serial Number:      S13PJ1KQ212924      
	Firmware Revision:  1AA01108
Standards:
	Used: ATA-8-ACS revision 3b 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 1953525168
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1000*1000:     1000204 MBytes (1000 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: disabled
	Recommended acoustic management value: 254, current value: 128
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 udma7 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	    	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
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
	    	Media Card Pass-Through
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	unknown 76[12]
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
Security: 
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	172min for SECURITY ERASE UNIT. 172min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000f00b129242
	NAA		: 5
	IEEE OUI	: f0
	Unique ID	: 0b129242
Checksum: correct

```

---

### Post by FuturePusher on 2009-09-17
An old thread, but this answer is still useful for people (looking for &) finding it:

Under conditions such as the original poster's, and more conditions where the issue may mainly be due to hdparm not being able to issue certain commands to drive, do this to research it all...

```
hdparm -B 240 /dev/sd?
```

(replace the "?" with the drive letter in question.)

What that does: it tells hdparm to try and set an "Advanced Power Management" level of 240, which is one of the least "aggressive" levels most drives can do, without disabling APM all together.

If You get an error message after that, it most likely means Your drive and it's features are newer, or working in newer ways, than Your current hdparm recognizes - at least i feel pretty certain that's the issue.

Remedy it with either manually upgrading Your version of hdparm with the freshest available (look around online at Freshmeat/Sourceforge)... or just "wait it out", as in waiting for Your distribution to pick up a newer version handling Your specific drive better.

---

