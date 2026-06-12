---
title: "Slow e-sata?"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by WakkiTabakki on 2008-03-21
Hi all
I just bought a WD MyBook 500Gb with firewire/usb/e-sata interface and it works just fine (under linux, windows on the other hand completely freezes when I disconnect it, but thats another story :p).

I now have it connected via the e-sata interface and copied about 2 Gb of data to it, and it seems to be really slow. Roughly 12-13 Mb/s...
Running hdparm -Tt revealed:
```
/dev/sdd:
 Timing cached reads:   1976 MB in  2.00 seconds = 988.61 MB/sec
 Timing buffered disk reads:  218 MB in  3.00 seconds =  72.55 MB/sec
```

And hdparm -I
```
/dev/sdd:

ATA device, with non-removable media
	Model Number:       WD My Book                              
	Serial Number:      WD-WCASU0474982
	Firmware Revision:  01.01B01
Standards:
	Used: ATA/ATAPI-6 T13 1410D revision 1 
	Supported: 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  976773168
	device size with M = 1024*1024:      476940 MBytes
	device size with M = 1000*1000:      500107 MBytes (500 GB)
Capabilities:
	LBA, IORDY(cannot be disabled)
	Queue depth: 1
	Standby timer values: spec'd by Vendor, with device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	48-bit Address feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART self-test
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
Integrity word not set (found 0x0000, expected 0xdfa5)

```
From what I can see everything is dandy... NCQ, DMA and all is fine, still the write speed is actualyl  slower than USB2 specs...

Am I missing something?
/N 

Specs:
Hardy Heron (all updates applied as of 2008-03-21)
Computer: [ASUS T3-M2NC51PV]("http://uk.asus.com/products.aspx?l1=1&l2=2&l3=407&l4=0&model=1155&modelmenu=2")
In short:
Nvidia C51PV / MCP51
AMD X2 5600+

---

### Post by WakkiTabakki on 2008-04-04
No one?

---

### Post by OoooMatron on 2008-05-02
I have the same problem with the 1TB edition. I formatted mine to ext3 but it transfers around 7mb/s!

---

### Post by WakkiTabakki on 2008-05-04
Found another thread about the same problem, no solution (yet) though:
[http://ubuntuforums.org/showthread.php?t=776192](http://ubuntuforums.org/showthread.php?t=776192)


/N

---

### Post by caladeira on 2008-06-10
Hello!

Well I have the same hardware (ASUS T3-M2NC51PV) and I've never used a E-sata drive.

However, I've already used USB drives that are terrible slow and also had some problems with other USB devices.

I have a wireless keyboard + mouse that never works during POST.
Only after the OS gets active (ubuntu or vista) the keyboard/mouse start working.
I've already tried this keyboard/mouse on other computers with no problem.
I've updated to the last BIOS version (0502 BIOS, latest beta bios!) and no better.

As far as I can tell, this peace of hardware (ASUS T3-M2NC51PV) is very bad and may be the source of your problem.

Probably this was my last ASUS buy.

Best regards.

---

