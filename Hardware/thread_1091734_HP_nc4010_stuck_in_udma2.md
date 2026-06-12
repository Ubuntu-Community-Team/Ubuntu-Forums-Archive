---
title: "HP nc4010 stuck in udma2"
date: 2009-03-09
forum: Hardware
---

### Post by Kang on 2009-03-09
Well, as the title indicates my nc4010 is stuck in udma2, and obviously every operation involving HDD (Seagate ST9808211A) is very slooooow. I tried switching to udma5 (that's the fastest mode this disk can work in), but all I get is errors:

```
kang@nc4010:~$ sudo hdparm -d1 -X69 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting xfermode to 69 (UltraDMA mode5)
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Read timings:

```
kang@nc4010:~$ sudo hdparm  -tT /dev/sda

/dev/sda:
 Timing cached reads:   214 MB in  2.00 seconds = 106.87 MB/sec
 Timing buffered disk reads:   10 MB in  3.46 seconds =   2.89 MB/sec

```

Here's my hdparm -I output:

```
/dev/sda:

ATA device, with non-removable media
	Model Number:       ST9808211A                              
	Serial Number:      3LG0KPZ0
	Firmware Revision:  3.00    
Standards:
	Used: ATA/ATAPI-6 T13 1410D revision 2 
	Supported: 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	17475
	heads		16	15
	sectors/track	63	63
	--
	CHS current addressable sectors:   16513875
	LBA    user addressable sectors:  156301488
	device size with M = 1024*1024:       76319 MBytes
	device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
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
	    	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	SMART error logging
	   *	SMART self-test
	   *	IDLE_IMMEDIATE with UNLOAD
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 0
Checksum: correct

```

And my lspci output:

```
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 USB Controller: NEC Corporation USB (rev 43)
00:12.1 USB Controller: NEC Corporation USB (rev 43)
00:12.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:13.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 03)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

Please help :-)

---

### Post by Kang on 2009-03-11
Shameless bump :oops:

---

### Post by buelligan on 2009-04-01
I think I'm having a  similar problem.  I'm trying to run Audacity on the following system:

Ubuntu 8.04 (Hardy)
Kernel 2.6.24-23-generic
Gnome 2.22.3

Hardware: Memory 947.6 MB
Processor: AMD Sempron 2400+

On the Audacity forum, someone indicated that very slow performance running this app was likely caused by DMA being inactive.  I tried the hdparm -d1 command as root and got the same inappropriate ioctl message as my fellow sufferer Kang.  

I should mention that audacity is the only app that I have trouble with.  Any help would be greatly appreciated.

Thanks,
buelligan

---

### Post by buelligan on 2009-04-01
I should have listed the results of my hdparm -I:
/dev/sdb1:

ATA device, with non-removable media
        Model Number:       WDC WD1200JD-22HBC0
        Serial Number:      WD-WCAL96550035
        Firmware Revision:  08.02D08
Standards:
        Supported: 6 5 4
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  234441648
        LBA48  user addressable sectors:  234441648
        device size with M = 1024*1024:      114473 MBytes
        device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    SATA-I signaling speed (1.5Gb/s)
           *    Host-initiated interface power management
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct
henry@henry-desktop:~$           

I assume that UDMA 6 is a slower protocol. (Should have put a newb warning on my first post; sorry).  

Anyway, I'm wondering why only Audacity (1.3.4) is affected.  
Any advice greatly appreciated,
buelligan

---

### Post by Kang on 2009-04-13
You're in udma6 mode, the fastest mode. So, your problem must be elsewhere...

---

### Post by buelligan on 2009-04-14
Thanks Kang,):P I'll check out the Audacity forum some more.

---

### Post by Marran77 on 2010-02-07
There is a thread on the hp-laptop support page or similar (can't remember the name right now, but you can access it through the HP home page) that is dealing with the nc4010. It says that there is a bug (I think it was) in the BIOS. It can't handle larger partitions than 80 GB. It has something to do with the DMA. But I see your HDD is only 80GB so it should'nt affect you. 

I however have 160GB. I made three partitions on the disk. And it has improved the speed of the harddrive.

Don't know if this makes things clearer, but but...

---

