---
title: "Hard Drive / Reinstall / DTR / Slow /"
date: 2008-08-06
forum: General Help
---

### Post by benign on 2008-08-06
I'm going to do a complete reinstall since I can't get my sound working and the GUI is acting very screwy after downloading a bunch of updates from the update manager. Is it just me or when you download a bunch of pending updates at the same time, it screws up the whole system? This is the third time it has happened to me after telling myself, "What harm can official updates do?" How do you turn the update notification off??

Beyond that, I'm trying to back up 15 or so gigs and my transfer rate is beginning at ~20MB/s and after a minute or two it goes down to 4 or even 2! I'm transfering the files across the same hard disk from ext3 to ntfs. 

What's causing this? This drive should be lightning fast but it feels like I have a floppy disk in there. I looked into hdparm and have the following info:

```

sean@ubuntu:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=Hitachi HDT725032VLA380                 , FwRev=V54OA7BA, SerialNo=      VFA200R2316WAA
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7372kB, MaxMultSect=16, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```

```

sean@ubuntu:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1368 MB in  2.00 seconds = 683.92 MB/sec
 Timing buffered disk reads:  220 MB in  3.01 seconds =  73.12 MB/sec

```

```

sean@ubuntu:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0

```

```

sean@ubuntu:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       Hitachi HDT725032VLA380                 
	Serial Number:      VFA200R2316WAA
	Firmware Revision:  V54OA7BA
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 1 
	Supported: 7 6 5 4 & some of 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  625142448
	device size with M = 1024*1024:      305245 MBytes
	device size with M = 1000*1000:      320072 MBytes (320 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 1
	Advanced power management level: disabled
	Recommended acoustic management value: 128, current value: 128
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	    	64-bit World wide name
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	Non-Zero buffer offsets in DMA Setup FIS
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	    	In-order data delivery
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
Checksum: correct

```

```

sean@ubuntu:~$ sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default) 
16-bit)

```

```

sean@ubuntu:~$ dmesg | grep -i ata
[    0.000000]  BIOS-e820: 0000000037ef3000 - 0000000037f00000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   29.120711] Memory: 890932k/916416k available (2489k kernel code, 25096k reserved, 1318k data, 320k init)
[   32.241204] libata version 3.00 loaded.
[   33.018599] sata_nv 0000:00:0e.0: version 3.5
[   33.020056] scsi0 : sata_nv
[   33.020109] scsi1 : sata_nv
[   33.020290] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe400 irq 20
[   33.020293] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe408 irq 20
[   33.484726] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   33.492850] ata1.00: ATA-7: Hitachi HDT725032VLA380, V54OA7BA, max UDMA/133
[   33.492853] ata1.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   33.509836] ata1.00: configured for UDMA/133
[   33.976086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   34.141007] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H653L, 0514, max UDMA/33
[   34.141012] ata2.00: applying bridge limits
[   34.312806] ata2.00: configured for UDMA/33
[   34.312927] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   34.314205] scsi2 : sata_nv
[   34.314268] scsi3 : sata_nv
[   34.314440] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xd000 irq 23
[   34.314442] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xd008 irq 23
[   34.624241] ata3: SATA link down (SStatus 0 SControl 310)
[   34.943826] ata4: SATA link down (SStatus 0 SControl 310)

```

```

sean@ubuntu:~$ dmesg | grep -i dma
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3076 pages used for memmap
[    0.000000]   DMA32 zone: 221932 pages, LIFO batch:31
[    0.000000] Policy zone: DMA32
[   32.834983] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   33.020290] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe400 irq 20
[   33.020293] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe408 irq 20
[   33.492850] ata1.00: ATA-7: Hitachi HDT725032VLA380, V54OA7BA, max UDMA/133
[   33.509836] ata1.00: configured for UDMA/133
[   34.141007] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H653L, 0514, max UDMA/33
[   34.312806] ata2.00: configured for UDMA/33
[   34.314440] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xd000 irq 23
[   34.314442] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xd008 irq 23

```

Does anything there stick out like a sore thumb as the culprit? Any help at all would be appreciated.

edit: OH before I screw something up. I'm reinstalling Hardy on the same drive as Vista with duel boot setup. Is this reinstall going to screw with grub at all?

---

### Post by kihjin on 2008-08-06
Did your drive ever transfer 'normal speed' in Ubuntu? I looked at your config and nothing stands out as being the cause. 

Also you can skip the installation of a boot loader during your reinstall, but I suggest backing up your menu.lst anyway if you want to avoid having to rewrite it.

---

