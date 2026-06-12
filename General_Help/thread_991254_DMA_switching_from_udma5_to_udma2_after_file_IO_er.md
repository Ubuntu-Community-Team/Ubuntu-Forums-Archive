---
title: "DMA switching from udma5 to udma2 after file I/O error"
date: 2008-11-23
forum: General Help
---

### Post by Pilot_51 on 2008-11-23
I'm rather new to Linux, about 5 months on Ubuntu as server and secondary OS, so please bear with me.

I have a server box running Ubuntu 8.10 Desktop Edition and I've been having a problem with hard disk activity causing the system to lag badly, mouse and everything.

I have a 160GB PATA hard drive (ATA100 controller) with multiple partitions including NTFS.
The motherboard is a Shuttle AK32L with a VIA VT8233 southbridge.

After finding out about hdparm and testing the drive, I've found that it was running on udma2.
```
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   176 MB in  2.01 seconds =  87.41 MB/sec
 Timing buffered disk reads:    8 MB in  3.69 seconds =   2.17 MB/sec
```
```
sudo hdparm -I /dev/sda
/dev/sda:

ATA device, with non-removable media
	Model Number:       SAMSUNG SP1614N                         
	Serial Number:      S016J10X509293      
	Firmware Revision:  TM100-24
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	65535
	heads		16	1
	sectors/track	63	63
	--
	CHS current addressable sectors:    4128705
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  312581808
	device size with M = 1024*1024:      152627 MBytes
	device size with M = 1000*1000:      160041 MBytes (160 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
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
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	56min for SECURITY ERASE UNIT. 56min for ENHANCED SECURITY ERASE UNIT.
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by CSEL
Checksum: correct
```

I tried switching it back to udma5...
```
sudo hdparm -X69 /dev/sda

/dev/sda:
 setting xfermode to 69 (UltraDMA mode5)
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error
```

Modified /etc/modules:
```
fuse
lp
#custom start
amd74xx
mousedev
psmouse
via82cxxx
piix
ide-core
#ide-generic
ide-disk
ide-cd
#custom end
```

Added to /etc/hdparm.conf:
```
/dev/sda {
	dma = on
	io32_support = 1
	write_cache = on
}
```

After rebooting, DMA was back up at udma5.
```
sudo hdparm -i /dev/sda

/dev/sda:

 Model=SAMSUNG SP1614N                         , FwRev=TM100-24, SerialNo=S016J10X509293      
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=65535/1/63, CurSects=4128705, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```
```
sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   448 MB in  2.01 seconds = 223.26 MB/sec
 Timing buffered disk reads:  170 MB in  3.03 seconds =  56.03 MB/sec
```

Then when I tried copying a large folder from an NTFS partition to an ext3 partition, a file encountered an I/O error, and that's when it went back to udma2. It appears to be a specific file causing the error, in this case it's a map for a Half-Life 2 mod which I was planning to set up a server, so it's easily replaceable.

Anyway, basically what I'm asking, is there a way to prevent DMA from switching to a slower mode when it encounters an I/O error on a file? Or if not that, is there at least a way to switch it back to udma5 without rebooting? The I/O errors appear (I'm hoping) to be isolated file corruption rather than a problem with the actual hardware, something bound to happen to anyone from time to time. It works perfectly fine on udma5 until it hits a bad file and switches to udma2.
Also does anyone have suggestions for tools to check and fix drive/file problems?

Let me know if any more info is needed, I don't want to fill the first post with too many unnecessary details.

---

### Post by trashmonkey on 2009-04-23
I'm having the same issue. I have two semi identical drives in a software RAID configuration.  The first drive /dev/sda drops back down to UDMA2, while /dev/sdb stays at UDMA5.  Boot time is fantastic, but as soon as I launch any application, sda drops back down to UDMA2.

sudo hdparm -I /dev/sda gives me:

/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD400BB-00DEA0                      
	Serial Number:      WD-WCAD1A113075
	Firmware Revision:  05.03E05
Standards:
	Supported: 5 4 3 
	Likely used: 6
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:   78165360
	device size with M = 1024*1024:       38166 MBytes
	device size with M = 1000*1000:       40020 MBytes (40 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	bytes avail on r/w long: 40
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
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
	    	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	SMART error logging
	   *	SMART self-test
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


sudo hdparm -I /dev/sdb gives me:

/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD400BB-22JHA0                      
	Serial Number:      WD-WCAMA1254661     
	Firmware Revision:  05.01C05
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
	LBA    user addressable sectors:   78165360
	device size with M = 1024*1024:       38166 MBytes
	device size with M = 1000*1000:       40020 MBytes (40 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	SMART error logging
	   *	SMART self-test
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by the jumper
Checksum: correct

As I just ran this, sdb dropped down to udma4

I have followed this thread's instructions as well as this one from wallneradam:  [http://ubuntuforums.org/archive/index.php/t-415057.html](http://ubuntuforums.org/archive/index.php/t-415057.html)

HELP!!!

---

### Post by trashmonkey on 2009-04-23
Ha ha!  I think that I just fixed it.  With the help from above and this forum:  [http://ubuntuforums.org/archive/index.php/t-678153.html](http://ubuntuforums.org/archive/index.php/t-678153.html) and with help from satreth, I think I finally have it taken care of.  

I blacklisted ata_generic and added pata_atiixp to /etc/initramfs-tools/modules

pata_atiixp
blacklist ata_generic

and recreated the initramfs with

sudo update-initramfs -u

and, after a reboot, the speed was better :

At least UDMA5 is staying enabled for both drives.

---

### Post by trashmonkey on 2009-04-23
Never mind, still back at square one.  Upgraded to 9.04 today still with no luck.

---

### Post by trashmonkey on 2009-08-10
No more issues, I read in another thread that it was a HD failing so I replaced the HD that kept reverting back to UDMA2 and voila!  No more slowdowns or gray screens!

---

