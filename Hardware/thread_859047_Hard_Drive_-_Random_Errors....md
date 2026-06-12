---
title: "Hard Drive - Random Errors..."
date: 2008-07-14
forum: Hardware
---

### Post by kripkenstein on 2008-07-14
I have a new computer, and I have the following odd behavior. On Windows it works fine (which I installed just to test things, after I ran into the following problems), but in Ubuntu I get random hard drive errors. At first I would just get strange behavior that I couldn't figure out, but now I have the following test, what I did was this:

I compiled a project hundreds of times and md5sum-ed the output, to see if it was the same. When run on a ramdrive (that is, all the source files are on the ramdrive and I compile on the ramdrive as well, this is on /dev/shm), I get the exact same result every time. But on the hard drive, I get around 20% failures. A failure might be even a single wrong byte, I guess, all I know is that the md5sum is different. This is on files of size 6MB, so, perhaps one wrong byte per 30MB or so?

Again, what is strange is that the drive works fine in Windows, it's only on Ubuntu that I get these errors. This is on Hardy, but I get the same in Fedora, so I guess it's a general Linux issue?

If anyone has any ideas what might be the issue, I'd appreciate it. This is driving me nuts... and of course the store won't replace anything because "it works fine in Windows, so the hardware is fine".

The machine is a Core 2 Duo E8400, Gigabyte EP35-DS3L motherboard, 4GB RAM, and the hard drive is a [WD Caviar Blue 250 GB]("http://www.wdc.com/en/products/products.asp?DriveID=298").

Here are my hdparm results, I don't even know what to look for myself, but maybe it's relevant:
```

$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD2500AAKS-00B3A0                   , FwRev=01.03A01, SerialNo=     WD-WMAT11662633
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD2500AAKS-00B3A0                   
	Serial Number:      WD-WMAT11662633
	Firmware Revision:  01.03A01
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  488397168
	device size with M = 1024*1024:      238475 MBytes
	device size with M = 1000*1000:      250059 MBytes (250 GB)
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
	    	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	54min for SECURITY ERASE UNIT. 54min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee0ab401e26
	NAA		: 5
	IEEE OUI	: 14ee
	Unique ID	: 0ab401e26
Checksum: correct

```
Thanks in advance!

---

### Post by Dougie187 on 2008-07-14
Are you sure its the hard drive?

Did you do the same test in windows?

Also, what type of project are you compiling? And what Compiler are you using to complile it? (versions as well)

I'm thinking, that if you have the same issue in both linux distributions and not in the windows one, then it might be a compiler issue. But im not really sure. But if that is the case, I have a hard time believing that its a hard drive issue.

---

### Post by kripkenstein on 2008-07-14
> **Dougie187 said:**
> Are you sure its the hard drive?

Did you do the same test in windows?

Also, what type of project are you compiling? And what Compiler are you using to complile it? (versions as well)

I'm thinking, that if you have the same issue in both linux distributions and not in the windows one, then it might be a compiler issue. But im not really sure. But if that is the case, I have a hard time believing that its a hard drive issue.

Well, it's hard to do the exact same test in Windows, I don't even know how to compile things there. But I guess I can try. However, I used Windows for days and encountered no errors, while running for a few hours on Hardy leads to problems (downloaded files are corrupt and other strange and random stuff).

The compilation on Linux was using the default compiler in Hardy, says it is gcc 4.2.3. I'm compiling Sauerbraten, a nice FPS game. Takes around 1-2 minutes to compile, binary is around 6 MB at the end.

The reason I think it is a hard drive issue is that when I compile on a ramdrive then it goes well 100% of the time. Only compiling on the hard drive fails. These are the exact same sources, same machine, and same compiler, so I don't think the compiler is at fault. The only difference is one thing is all in RAM, the other is on the hard disk.

Also, I tested my CPU and RAM extensively using memtest and memtest+, also cpuburn, and found 0 errors, so I don't think it is a CPU or RAM issue. It all seems to point to a hard drive problem at this point, but I'm no expert and I'm just guessing, so tell me if that makes sense or not.

---

### Post by Odrodzona-Sarmacja on 2008-07-14
On some hardware configurations Linux hate ext3 file system. It's the kernel bug. Even Linus Thorvald knows about it last few years and still did nothing about it.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102)

Enjoy this reading and your Linux OS.

---

### Post by kripkenstein on 2008-07-14
> **Odrodzona-Sarmacja said:**
> On some hardware configurations Linux hate ext3 file system. It's the kernel bug. Even Linus Thorvald knows about it last few years and still did nothing about it.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102)

Enjoy this reading and your Linux OS.

Thanks for the info. That was certainly a depressing read, those are serious bugs... I'm not sure they are related to my problems, however, they say entire filesystems get corrupted, can't be mounted, etc., when I have just minor random errors when saving files.

---

### Post by Daelyn on 2008-07-15
The bug seems to only be present in 64bit systems with AMD CPU's.
And, from what I gather, you don't have that.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)

---

### Post by Odrodzona-Sarmacja on 2008-07-15
I have AMD CPU, Athlon XP 2.5Ghz and even if it is only 32bit CPU I am also having these issues. Corruption occurs when downloading files into ext3 partition, so even a simple software update can send entire computer into hard drive lockup and need to reboot and need to run fsck (sometimes even manually). I use also 32bit i386 version of Xubuntu and not 64bit, as it doesn't run on my Athlon XP.

---

### Post by kripkenstein on 2008-07-15
Ok, my problem isn't the hard drive, and isn't ext3 either: I get the same errors on a USB flash drive.

So, when I compile in a ramdrive, all is well, but the hard drive and flash drive give corrupt results sometimes.

I am baffled, any idea what the problem could be?

---

