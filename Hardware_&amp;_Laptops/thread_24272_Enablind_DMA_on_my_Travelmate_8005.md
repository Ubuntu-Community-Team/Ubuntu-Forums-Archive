---
title: "Enablind DMA on my Travelmate 8005"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by mirtux on 2005-04-06
Hi,
  i would like to enable DMA on my laptop since this is the results from **hdparm**:
 ```

hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   10 MB in  3.30 seconds =   3.03 MB/sec
```
very poor. 
However when i try to enable it with **hdparm -d1 /dev/hda** i've got the error:
 ```

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma	=  0 (off)

``` 
Maybe i've got some IDE module missing?

Regards,
MC

---

### Post by mirtux on 2005-04-06
This is my **hdparm -I /dev/hda**
 ```

/dev/hda:

ATA device, with non-removable media
	Model Number:	   TOSHIBA MK8025GAS					   
	Serial Number:	  748B0296S
	Firmware Revision:  KA023A  
Standards:
	Supported: 6 5 4 3 
	Likely used: 6
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA	user addressable sectors:  156301488
	device size with M = 1024*1024:	   76319 MBytes
	device size with M = 1000*1000:	   80026 MBytes (80 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	bytes avail on r/w long: 48	Queue depth: 1
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = ?
	Advanced power management level: unknown setting (0x0080)
	DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
		 Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
		 Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	NOP cmd
	   *	READ BUFFER cmd
	   *	WRITE BUFFER cmd
	   *	Host Protected Area feature set
	   *	Look-ahead
	   *	Write cache
	   *	Power Management feature set
		Security Mode feature set
	   *	SMART feature set
	   *	Mandatory FLUSH CACHE command 
	   *	Device Configuration Overlay feature set 
	   *	SET MAX security extension
	   *	Advanced Power Management feature set
	   *	SMART self-test 
	   *	SMART error logging 
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
	72min for SECURITY ERASE UNIT. 
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by the jumper
Checksum: correct

``` 

Regards,
MC

---

### Post by alastair on 2005-04-06
I assume you are trying to do this tuning as superuser i.e.

sudo hdparm -d1 /dev/hda

If so, it /might/ be that you are missing the right IDE chipset support (or similar). 

Do :

lspci -v

to see the IDE chipset you have, and :

lsmod

to see loaded modules.

Also, check the IDE messages on boot from :

/var/log/syslog

---

### Post by mirtux on 2005-04-07
Hi,
   this is the results of the IDE interface:
```

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03) (prog-if 8a [Master SecP PriP])
		Subsystem: Acer Incorporated [ALI]: Unknown device 0051
		Flags: bus master, medium devsel, latency 0, IRQ 6
		I/O ports at <unassigned>
		I/O ports at <unassigned>
		I/O ports at <unassigned>
		I/O ports at <unassigned>
		I/O ports at 1860 [size=16]
		Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
```
I'm trying to compile it with the Intel PIIX chipset (n kernel it is written that it support also ICH chipset).

I'll post here about the results...

Regards,
MC

---

### Post by mirtux on 2005-04-07
Hi,
   ok, i'm having DMA running using the PIIX kernel module :-P

 ```

/dev/hda:
 multcount	=  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq	=  0 (off)
 using_dma	=  1 (on)
 keepsettings =  0 (off)
 readonly	 =  0 (off)
 readahead	= 256 (on)
 geometry	 = 65535/16/63, sectors = 156301488, start = 0

 /dev/hda:
 Timing buffered disk reads:   78 MB in  3.01 seconds =  25.93 MB/sec

``` 

Thanks for help,
MC

---

