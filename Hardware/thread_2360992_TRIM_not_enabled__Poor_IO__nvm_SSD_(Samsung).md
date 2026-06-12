---
title: "TRIM not enabled?  Poor I/O?  nvm SSD (Samsung)"
date: 2017-05-10
forum: Hardware
---

### Post by dpcole72 on 2017-05-10
Hello.  I recently reinstalled Ubuntu 16.04.1 on my Dell Latitude laptop that has a Samsung 950 Pro 512GB PCIe M.2 NVMe Class 40 Solid State Drive.

When checking for TRIM, I get weird results:


sudo hdparm -I /dev/nvme0n1p2

/dev/nvme0n1p2:
SG_IO: questionable sense data, results may be incorrect

ATA device, with non-removable media
Standards:
	Likely used: 1
Configuration:
	Logical		max	current
	cylinders	0	0
	heads		0	0
	sectors/track	0	0
	--
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:           0 MBytes
	device size with M = 1000*1000:           0 MBytes 
	cache/buffer size  = unknown
Capabilities:
	IORDY not likely
	Cannot perform double-word IO
	R/W multiple sector transfer: not supported
	DMA: not supported
	PIO: pio0 


**AND**

 sudo hdparm -t /dev/nvme0n1p2

/dev/nvme0n1p2:
 Timing buffered disk reads: 3002 MB in  3.00 seconds = 1000.35 MB/sec


Seems a little slow for performance?  Is there a TRIM driver available since the -I parameter is returning "questionable sense data"...

Thanks!

---

### Post by efflandt on 2017-05-10
I could be wrong, but if you are looking for drive info, shouldn't you check the "drive" instead of a "partition" on the drive? Since I am not familiar with nvme devices I am guessing /dev/nvme0n1 instead of /dev/nvme0n1p2. For example this is an example of the beginning of -I info for mSATA SSD:```
$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
    Model Number:       Crucial_CT512M550SSD3                   
    Serial Number:      14370E4FCF3D
    Firmware Revision:  MU01    
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Used: unknown (minor revision code 0x0028) 
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 1000215216
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:      488386 MBytes
    device size with M = 1000*1000:      512110 MBytes (512 GB)
    cache/buffer size  = unknown
    Form Factor: less than 1.8 inch
    Nominal Media Rotation Rate: Solid State Device
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
```And farther down: Deterministic read ZEROs after TRIM

But it is in a SATA adapter connected with SATA2, so it is not nearly as fast as your M.2:
$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads: 726 MB in  3.00 seconds = 241.66 MB/sec

---

### Post by dpcole72 on 2017-05-10
Thanks for the info!

I got this as a result - some items look weird (foreign characters) but at least it appears TRIM is supported (though why my throughput is so low still remains a mystery):

> sudo hdparm -I /dev/sdb

/dev/sdb:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

ATA device, with non-removable media
	Model Number:       &#65533;&#65533;&#65533;|&#65533;&#65533;
                                     "4&#65533;@	&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;	&#65533;&#65533;
	Serial Number:      )3g&#65533;@&#65533;&#65533;`;<
	Media Serial Num:   &#65533;&#65533;&#65533;X6&#65533;0&#65533;&#65533;&#65533;	&#65533;&#65533;&#42761;&#65533;QD	&#65533;&#65533;~&#65533;&#65533;
	Media Manufacturer: &#65533;eA#&#65533;lV&#65533;0=&#65533;&#65533;
	Transport:          Parallel; Revision: 0xf42c
Standards:
	Used: unknown (minor revision code 0x50d0) 
	Supported: 14 12 11 10 9 7 6 
	Likely used: 14
Configuration:
	Logical		max	current
	cylinders	0	0
	heads		35489	0
	sectors/track	39192	0
	--
	Logical  Sector size:             373414402 bytes
	Physical Sector size:            2423685248 bytes
	Logical Sector-0 offset:         3918870568 bytes
	device size with M = 1024*1024:           0 MBytes
	device size with M = 1000*1000:           0 MBytes 
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: 4419
Capabilities:
	IORDY(cannot be disabled)
	Standby timer values: spec'd by Vendor
	R/W multiple sector transfer: Max = 255	Current = 255
	DMA: *mdma0 *mdma1 *mdma2 *mdma3 *mdma4 *mdma5 *mdma6 *mdma7 (?)
	     Cycle time: recommended=193ns
	PIO: pio0 pio1 pio2 pio5 pio6 pio7 
	     Cycle time: no flow control=35490ns  IORDY flow control=208ns
	   *	reserved 69[6]
	   *	DOWNLOAD MICROCODE DMA command
	   *	DEVICE CONFIGURATION SET/IDENTIFY DMA commands
	   *	CFast specification support
	   *	Data Set Management TRIM supported (limit 20154 blocks)
		Removable Media Status Notification feature set supported
Integrity word not set (found 0xb521, expected 0x93a5)


---

### Post by AlexToind on 2017-06-05
Hi dpcole72,

I'm facing the same "problem", but I do not understand if you have mounted your disk in /dev/sdb manually or if you have done something else.
This is my output (I have a [COLOR=#000000]M.2 NVMe[/COLOR] SSD installed in my Dell Precision 5520):
> 
sudo hdparm -I /dev/nvme0n1

/dev/nvme0n1:
SG_IO: questionable sense data, results may be incorrect

ATA device, with non-removable media
Standards:
    Likely used: 1
Configuration:
    Logical        max    current
    cylinders    0    0
    heads        0    0
    sectors/track    0    0
    --
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:           0 MBytes
    device size with M = 1000*1000:           0 MBytes 
    cache/buffer size  = unknown
Capabilities:
    IORDY not likely
    Cannot perform double-word IO
    R/W multiple sector transfer: not supported
    DMA: not supported
    PIO: pio0 



**EIDT: **on the other hand, it seems to trim properly: 
> 
sudo fstrim -av/: 914,3 GiB (981705830400 bytes) trimmed


---

