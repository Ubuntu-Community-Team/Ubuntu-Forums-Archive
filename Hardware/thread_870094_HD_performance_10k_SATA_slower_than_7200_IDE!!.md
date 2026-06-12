---
title: "HD performance 10k SATA slower than 7200 IDE!!"
date: 2008-07-25
forum: Hardware
---

### Post by Execute_Method on 2008-07-25
I have what seems to me like an odd issue. If anyone can help it would be greatly appreciated. I've been googling all morning trying to figure this one out.

sda = wd raptor 36gb 10k rpm 8mb cache
sdb = wd SATA 120gb 7200rpm 8mb cache
sdc = seagate PATA 160gb 7200rpm 2mb cache

here are the hdparm infos

```
/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD360GD-00FLA2                      
	Serial Number:      WD-WMAKE1873741
	Firmware Revision:  31.08F31
Standards:
	Supported: 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:   72303840
	LBA48  user addressable sectors:   72303840
	device size with M = 1024*1024:       35304 MBytes
	device size with M = 1000*1000:       37019 MBytes (37 GB)
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
	    	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Release interrupt
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	READ/WRITE_DMA_QUEUED
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Host-initiated interface power management
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
Security: 
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct

```

```
/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD1200JD-00GBB0                     
	Serial Number:      WD-WMAES1742336
	Firmware Revision:  02.05D02
Standards:
	Supported: 6 5 4 
	Likely used: 6
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  234441648
	LBA48  user addressable sectors:  234441648
	device size with M = 1024*1024:      114473 MBytes
	device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
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
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Host-initiated interface power management
	   *	Device-initiated interface power management
Security: 
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by the jumper
Checksum: correct

```
```
/dev/sdc:

ATA device, with non-removable media
	Model Number:       ST3160212ACE                            
	Serial Number:      5LSGV8XJ
	Firmware Revision:  3.ACB   
Standards:
	Supported: 7 6 5 4 
	Likely used: 7
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
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 160, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
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
	   *	DOWNLOAD_MICROCODE
	   *	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by CSEL
Checksum: correct

```

When I run cached and buffered tests, the 10k Sata(sda)drive performs slower than the 7200rpm IDE(sdc).

The 10k drive has The OS on it, and the other drives are backup. Could this be causing the difference I'm seeing?

The IDE drive is newer and came out of a **rectTV DVR. What could be the difference there, that makes it perform better than the Raptor? Ares there any settings to change for the Raptor with sdparm to get better performance?

Here are the test results:

```
/dev/sda1:
 Timing cached reads:   1130 MB in  2.00 seconds = 564.96 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.24 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sda1

/dev/sda1:
 Timing cached reads:   1138 MB in  2.00 seconds = 568.53 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.34 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sda1

/dev/sda1:
 Timing cached reads:   1130 MB in  2.00 seconds = 564.92 MB/sec
 Timing buffered disk reads:  186 MB in  3.00 seconds =  61.93 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1116 MB in  2.00 seconds = 557.26 MB/sec
 Timing buffered disk reads:  120 MB in  3.03 seconds =  39.64 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1124 MB in  2.00 seconds = 561.75 MB/sec
 Timing buffered disk reads:  122 MB in  3.04 seconds =  40.17 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1126 MB in  2.00 seconds = 562.55 MB/sec
 Timing buffered disk reads:  122 MB in  3.05 seconds =  40.06 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sdc1

/dev/sdc1:
 Timing cached reads:   1128 MB in  2.00 seconds = 563.75 MB/sec
 Timing buffered disk reads:  208 MB in  3.02 seconds =  68.95 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sdc1

/dev/sdc1:
 Timing cached reads:   1136 MB in  2.00 seconds = 567.86 MB/sec
 Timing buffered disk reads:  208 MB in  3.01 seconds =  69.14 MB/sec
stephen@ubuntu:~$ sudo hdparm -t -T /dev/sdc1

/dev/sdc1:
 Timing cached reads:   1146 MB in  2.00 seconds = 573.04 MB/sec
 Timing buffered disk reads:  206 MB in  3.01 seconds =  68.55 MB/sec
```

---

### Post by WestCoastSuccess on 2008-07-28
I'm sorry, I'm not qualified to answer your question, however the one thing which strikes me is the following on your 10k drive (sda):

```

Standards:
    Supported: 6 5 4 
    Likely used: 8
```I've searched a bit for the precise meaning of this but have been unable to find out anything significant, unfortunately. However I didn't come across any examples where the "Likely used:" wasn't one of the options under "Supported:".

---

