---
title: "How do I make DMA work? ( 8.04 )"
date: 2008-05-27
forum: Hardware
---

### Post by pdevries on 2008-05-27
I'm trying ubuntu.  I cannot figure out how to get dma to work on my hard disk drive.  Dma works fine on this computer on the other distro I'm running.  This is a desktop computer, not a laptop, but I don't see any other hardware forum.

Here is some hdparm information:

(Checking how fast the drive reads)
sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   626 MB in  2.00 seconds = 312.96 MB/sec
 Timing buffered disk reads:   12 MB in  3.08 seconds =   3.89 MB/sec

(Try to enable dma) 
sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma     =  0 (off)
 HDIO_SET_DMA failed: Operation not permitted


(Querying the drive) 
sudo hdparm -iI /dev/hda

/dev/hda:

 Model=WDC WD800JB-00JJC0, FwRev=05.01C05, SerialNo=WD-WCAM9M146468
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=66
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       WDC WD800JB-00JJC0                      
	Serial Number:      WD-WCAM9M146468
	Firmware Revision:  05.01C05
Standards:
	Supported: 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	4047
	heads		16	16
	sectors/track	63	255
	--
	CHS current addressable sectors:   16511760
	LBA    user addressable sectors:  156301488
	device size with M = 1024*1024:       76319 MBytes
	device size with M = 1000*1000:       80026 MBytes (80 GB)
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
	    	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	SMART error logging
	   *	SMART self-test
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
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

I'd appreciate help in how to enable dma.

Thanks.

---

### Post by wabbalee on 2008-05-27
i dont have a ubuntu system to check it for you as i am now on kubuntu8.04 where i cannot find thid feature, but i remember that on ubuntu there is a setting in the gui that you can just enable hparm by placing a tick. it is either in system->preferences or in system->administration. that's the best i can do, may be another and more advanced user here can be of better help.

---

### Post by pdevries on 2008-05-27
Um, I think I found the problem.

My via ide hardware seems to require the kernel to be compiled with

CONFIG_BLK_DEV_VIA82CXXX=y

but, in the kernel supplied by ubuntu it has

CONFIG_BLK_DEV_VIA82CXXX is not set.

I don't believe the kernel will permit that driver to build as a module.

Is there any way to enable my dma without compiling my own kernel?  

If I compile my own kernel, am I correct that the package tools are no longer going to manage my kernel?  Will I also have to manually compile and install the modules for 3rd party applications like VirtualBox?

Thanks.

---

### Post by jocko on 2008-05-27
> **pdevries said:**
> Will I also have to manually compile and install the modules for 3rd party applications like VirtualBox?

Yes, you would have to rebuild all modules that are not provided by the kernel source itself.
For virtualbox it depends on which version you use.
The OSE version in the repo comes with precompiled module packages for the ubuntu kernels, so I think that would not work any more.
The restricted licence version of virtualbox will actually compile its modules when you install it, and I *think* it will automatically compile new modules if the kernel is updated (at least if you have the packages "build-essential", "linux-headers-generic" and "dkms" installed).

---

### Post by pdevries on 2008-05-28
I know how to do this myself, and how to manage it, but I thought the whole point of ubuntu was that I wouldn't have to.

Is this a bug?

---

### Post by jocko on 2008-05-28
> **pdevries said:**
> Is this a bug?
If a piece of hardware is not working properly, yes, it's a bug.
Report it to [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu). I guess the bug should be filed against the kernel (but search launchpad for via82cxxx, there seems to be some bugs already reported, e.g [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217511](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217511))

---

