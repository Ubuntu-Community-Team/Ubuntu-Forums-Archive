---
title: "Inconsistent SSD throughput"
date: 2009-10-10
forum: Hardware
---

### Post by apocalypse80 on 2009-10-10
I'm running a 160GB Intel x25-m G2 SSD in an HP elitebook 8530p and I'm getting wildly inconsistent maximum throughput under ubuntu jaunty.

The symptoms:

I ran a couple of copy-paste tests multiple times under ubuntu and windows XP, always copying from the ssd to itself.
- small files copy (3GB - 100000 files)
Perfectly consistent under both OS : ~18 MB/s under windows, ~30 MB/s under ubuntu
- large file copy (4GB - single file)
Perfectly consistent under windows : ~70 MB/s
Under jaunty it will either go through the entire process at ~65 MB/s or at ~40 MB/s (monitored via iotop).

hdparm -t shows a very similar thing, it will either produce a number ~250MB/s or one around 140MB/s.
hdparm -t --direct always goes to ~250MB/s.
Bootchart also shows sustained read speeds of ~270MB/s during readahead.
Extracting zip files (tiny zip files including humongous text files) produces write speeds around 90MB/s (iotop) which is fine.

For reference; windows synthetic benchmarks put maximum sequential throughput at 260/90 MB/s read/write.

The drive was partitioned by win7 - all partitions are aligned.
Ubuntu 9.04 is sitting on ext4 with the noatime option and I'm using the noop scheduler (though it didn't change things).

hdparm -I output

```

/dev/sda:

ATA device, with non-removable media
	Model Number:       INTEL SSDSA2M160G2GC                    
	Serial Number:      CVPO930600GU160AGN  
	Firmware Revision:  2CV102G9
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
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
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  312581808
	device size with M = 1024*1024:      152627 MBytes
	device size with M = 1000*1000:      160041 MBytes (160 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
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
	   *	SET_MAX security extension
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
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
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
Logical Unit WWN Device Identifier: 5001517958f99708
	NAA		: 5
	IEEE OUI	: 1517
	Unique ID	: 958f99708
Checksum: correct

```


I'm guessing it's not a normal deficiency of ext4 since it can actually get pretty much the same speed as windows/ntfs.
The drive seems to be working perfectly under most scenarios apart from large file copying.
The symptoms seem to indicate a sata controller issue.
Any ideas?

---

### Post by apocalypse80 on 2009-10-26
Just in case anyone is interested, the culprit is power management.
With "performance" (cpu at 2.53Ghz) I get full performance out of the ssd, with "ondemand" (cpu at 800Mhz) I get a huge performance hit.

Now who would have thought that copy-pasting would be cpu-limited?

---

