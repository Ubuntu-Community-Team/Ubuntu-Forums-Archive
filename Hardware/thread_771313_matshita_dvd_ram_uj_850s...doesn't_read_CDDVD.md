---
title: "matshita dvd ram uj 850s...doesn't read CD/DVD"
date: 2008-04-27
forum: Hardware
---

### Post by nu-kid on 2008-04-27
I have a System76 Laptop w/matshita dvd ram uj 850s. For some reason no matter what CD I put in it doesn't allow me to browse the contents, it only says there's a blank CD as if it's ready to be burned. Even CD's that have data already there appear the same way. With DVD movies it doesn't respond at all. Has anyone seen this before?!!!

Thnx

---

### Post by tedmasterweb on 2009-11-26
I have the same system and a similar problem however, my specific issue is that I am unable to burn iso images (or any data) to a DVD-R disc. The specific error I get is:

```
:-( /dev/scd0: media is not recognized as recordable DVD: 0
```

This used to work but at some point in the past year (possibly less) it stopped working. I know this for a fact because I still have the DVDs I burned about a year ago and the script I used to do the burning. The command was:

```
growisofs -dvd-compat -Z /dev/scd0=ubuntu-9.10-dvd-i386.iso
```

I am running Linux kernal 2.6.24-25-server Debian version lenny/sid. I tried burning a CD-R with apparent success, but the media is unreadable on my Macintosh, so, maybe I just burned it incorrectly. I have been unable to test with DVD+R or with DVD+RW as I do not keep a stock of such discs (especially since my DVD-R were working just fine).

I'm going to guess this is a driver issue, that an update to a driver in a recent system update introduced this incompatibility. The test would be to reinstall the system from the system disc sent by System76 using their original drivers, but I have to back up the entire system first (grrrr...)

Here is some specific info about my drive.

```
sudo hdparm -iI /dev/dvdrw

/dev/dvdrw:

 Model=MATSHITADVD-RAM UJ-875S                 , FwRev=1.00    , SerialNo=            fG51D4D9
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


ATAPI CD-ROM, with removable media
	Model Number:       MATSHITADVD-RAM UJ-875S                 
	Serial Number:      fG51D4D9
	Firmware Revision:  1.00    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
HW reset results:
	CBLID- above Vih
	Device num = 1

```

There is a similar thread here: [http://ubuntuforums.org/showthread.php?t=913975]("http://ubuntuforums.org/showthread.php?t=913975")

---

