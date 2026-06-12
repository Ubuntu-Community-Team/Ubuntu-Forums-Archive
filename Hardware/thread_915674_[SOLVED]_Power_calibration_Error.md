---
title: "[SOLVED] Power calibration Error?"
date: 2008-09-10
forum: Hardware
---

### Post by Yezinki on 2008-09-10
Hi there,

On my Sony vaio VGC-LS1 I have a Matshita UJ 846S slot loading DVD-RAM drive.

It can only read CDs.

Won't write a DVD of any kind/format, using K3b or Nero.

Sony support says try different media....I have tried most brands new blank media.

Nero Error is: Power Calibration Error?

Sony support says that it aint getting enough infrared to burn.......

This was my first time using this drive since I bought.......usually use my Dell with a Toshiba DVDRW drive no issues?

Well I did change the memory from @557 to @667 coz I had 2 X 1 GB modules lying free.

Hoping to hear your comments,

Regards!!

---

### Post by IntuitiveNipple on 2008-09-10
What report do you get from this:
```

lshal -u $(lshal | sed -n "s/^udi = '\(.*846S.*\)'/\1/p")

```

---

### Post by Yezinki on 2008-09-10
Thanks for that command.

I'll let you know as soon as I am done installing Ubuntu Hardy.


Just finished with XP MCE.....I tried another thing since it reads any brand, even scratchy CDs, tried to burn a new blank Verbatim CR-R...no problem it did it.

The question is it wont read or write DVDs....?

I shall run this command after I am done with Ubuntu & will try burning a DVDRW.

Regards!

---

### Post by Yezinki on 2008-09-10
**Earlier Errors:**




System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- unimplemented command-line option for this media.
- you have the option to re-run /usr/bin/dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -force=full /dev/scd0




System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
Unknown

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Embarrassed LOAD TRAY failed with SK=5h/ASC=24h/ACQ=00h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:672402 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m



System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- unimplemented command-line option for this media.
- you have the option to re-run /usr/bin/dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -force=full /dev/scd0



System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
Unknown

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: pre-formatting blank DVD+RW...
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
Embarrassed WRITE@LBA=0h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:672402 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m




Now I get this errror using a Sony DVD+R................

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
    1572864/1377079296 ( 0.1%) @0.0x, remaining 72:52 RBU 100.0% UBU   2.1%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 131:10 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 174:54 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 218:37 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 276:55 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 320:39 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 364:23 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 422:41 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 466:24 RBU 100.0% UBU 100.0%
    1572864/1377079296 ( 0.1%) @0.0x, remaining 510:08 RBU 100.0% UBU 100.0%
Embarrassed WRITE@LBA=300h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: closing track
Embarrassed CLOSE TRACK failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
/dev/scd0: closing disc
Embarrassed CLOSE DISC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:672402 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m

---

### Post by IntuitiveNipple on 2008-09-10
Looking at those errors I'd say there is a cable and/or power-supply issue to the drive.

Remove the back-panel and wiggle the connectors :)

---

### Post by Yezinki on 2008-09-10
Nero Error!




Windows XP 5.1
IA32
WinAspi: -

NT-SPTI used
Nero Version: 7.11.10.0
Internal Version: 7, 11, 10, 0
 (Nero Express)
Recorder:             <MATSHITA DVD-RAM UJ-846S>Version: F200 - HA 1 TA 0 - 7.11.10.0
 Adapter driver:      <IDE>                     HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default
CD-ROM:               <MATSHITA DVD-RAM UJ-846S >Version: F200 - HA 1 TA 0 - 7.11.10.0
 Adapter driver:      <IDE>                     HA 1

=== Scsi-Device-Map ===
CdRomPeripheral      : MATSHITA DVD-RAM UJ-846S         atapi Port 0 ID 0  DMA: On 
DiskPeripheral       : WDC WD2500JS-98NCB1              atapi Port 1 ID 0  DMA: On 

=== CDRom-Device-Map ===
MATSHITA DVD-RAM UJ-846S   F:   CdRom0
=======================

AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 2038MB (2087020kB)
Free physical memory: 1511MB (1548072kB)
Memory in use       : 25 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

7.9.2008
Burn DVD Image
10:16:52 AM	#1 Text 0 File SCSIPTICommands.cpp, Line 450
	LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	
10:16:52 AM	#2 Text 0 File Burncd.cpp, Line 3500
	Turn on Disc-At-Once, using DVD media
	
10:17:40 AM	#3 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2295103 (510:01.28, 4482MB)
	Last address to be written:             672401 (149:25.26, 1313MB)
	
10:17:40 AM	#4 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO (enabled: CD)
	
10:17:40 AM	#5 Text 0 File DlgWaitCD.cpp, Line 2988
	Recorder: MATSHITA DVD-RAM UJ-846S, Media type: DVD+RW
	 Disc Manufacturer ID: <MKM>, Media Type ID: <A02>, Product revision number: 0
	 Disc Application Code: 0, Extended Information Indicators: 1
	
10:17:40 AM	#6 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	Insert empty disc to write to.
		(Medium in drive: Unknown. Medium required by compilation: DVD R/RW, DVD DL, DVD-RAM.)
	
10:17:40 AM	#7 Text 0 File ThreadedTransferInterface.cpp, Line 778
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 672402 (672402) = #672402/149:25.27
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 672402 blocks [F: MATSHITA DVD-RAM UJ-846S]
	--------------------------------------------------------------
	
10:17:40 AM	#8 Text 0 File ThreadedTransferInterface.cpp, Line 979
	Prepare [F: MATSHITA DVD-RAM UJ-846S] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    1377079296, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |   672402 |   672402 | 0x00
	   672402 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
10:17:40 AM	#9 Text 0 File SCSIPTICommands.cpp, Line 240
	SPTILockVolume - completed successfully for FSCTL_LOCK_VOLUME
	
10:17:40 AM	#10 Text 0 File Burncd.cpp, Line 4286
	Caching options: cache CDRom or Network-Yes, small files-Yes (<64KB)
	
10:17:40 AM	#11 Phase 24 File dlgbrnst.cpp, Line 1767
	Caching of files started
	
10:17:40 AM	#12 Text 0 File Burncd.cpp, Line 4405
	Cache writing successful.
	
10:17:40 AM	#13 Phase 25 File dlgbrnst.cpp, Line 1767
	Caching of files completed
	
10:17:40 AM	#14 Phase 36 File dlgbrnst.cpp, Line 1767
	Burn process started at 4x (5,540 KB/s)
	
10:17:40 AM	#15 Text 0 File ThreadedTransferInterface.cpp, Line 2726
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
10:17:40 AM	#16 Text 0 File Cdrdrv.cpp, Line 10161
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD+RW (9), Part Version: 1.1x (2)
	 Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: re-writable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Physical Sector Number of Data Area:          26053F h
	 Data in Burst Cutting Area (BCA) does not exist
	  Disc Application Code: 0 / 0 h
	  Extended Information indicators: 1 h
	  Disc Manufacturer ID: MKM.....
	  Media type ID: A02
	  Product revision number: 0
	  Number of Physical format information bytes in use in ADIP up to byte 63: 57
	 Media Specific [16..783]:
	    00 00 01 4D 4B 4D 00 00 - 00 00 00 41 30 32 00 39    ...MKM.....A02.9
	    23 00 94 79 64 02 20 00 - 9C 7A 6C 02 20 00 9A 7B    #..yd....zl....{
	    68 02 20 12 12 10 E0 00 - F0 00 00 00 00 00 00 00    h...............
	    01 00 17 38 00 29 8B 3E - 02 24 00 2D 8E 38 02 24    ...8.).>.$.-.8.$
	    00 2C 90 3E 02 24 44 35 - 30 E0 F0 30 40 00 00 00    .,.>.$D50..0@...
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
10:17:40 AM	#17 Phase 98 File dlgbrnst.cpp, Line 1767
	Start formatting disc before burning
	
10:18:01 AM	#18 SPTI -1106 File SCSIPassThrough.cpp, Line 181
	CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1106)
	Sense Key:  0x03 (KEY_MEDIUM_ERROR)
	Sense Code: 0x73
	Sense Qual: 0x03
	CDB Data:   0x00 00 00 00 00 00 00 00 00 00 00 00 
	Sense Area: 0x71 00 03 00 00 00 00 0A 00 00 19 25 73 03 
	
10:18:01 AM	#19 Phase 101 File dlgbrnst.cpp, Line 1767
	Formatting disc failed
	
10:18:01 AM	#20 Text 0 File DVDPlusRW.cpp, Line 675
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
10:18:01 AM	#21 CDR -1106 File ThreadedTransferInterface.cpp, Line 1733
	**[SIZE="4"]Power calibration error[/SIZE]**	F: MATSHITA DVD-RAM UJ-846S
	
10:18:01 AM	#22 TRANSFER -27 File ThreadedTransferInterface.cpp, Line 1733
	Could not perform start of Disc-at-once
	
10:18:01 AM	#23 Text 0 File ThreadedTransfer.cpp, Line 268
	Pipe memory size 83836800
	
10:18:01 AM	#24 Phase 38 File dlgbrnst.cpp, Line 1767
	Burn process failed at 4x (5,540 KB/s)
	
10:18:01 AM	#25 Text 0 File SCSIPTICommands.cpp, Line 287
	SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
	
10:18:07 AM	#26 Text 0 File Cdrdrv.cpp, Line 11411
	DriveLocker: UnLockVolume completed
	
10:18:07 AM	#27 Text 0 File SCSIPTICommands.cpp, Line 450
	UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	

Existing drivers:

Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 0 (Security Option)

---

### Post by Yezinki on 2008-09-10
Do you think that changing the 2 GB physical RAM from @557 to @667 MHZ could be a reason too??

Regards!

---

### Post by IntuitiveNipple on 2008-09-10
Anything is possible. Try switching back to the original and see if the error clears up.

---

### Post by Yezinki on 2008-09-10
OK.......this is the log of sucessfully burnt CD-R.


Windows XP 5.1
IA32
WinAspi: -

NT-SPTI used
Nero Version: 7.10.1.0
Internal Version: 7, 10, 1, 0

Recorder:             <MATSHITA DVD-RAM UJ-846S>Version: F200 - HA 1 TA 0 - 7.10.1.0
 Adapter driver:      <IDE>                     HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> ATAPI, detected: ?
CD-ROM:               <MATSHITA DVD-RAM UJ-846S >Version: F200 - HA 1 TA 0 - 7.10.1.0
 Adapter driver:      <IDE>                     HA 1

=== Scsi-Device-Map ===
CdRomPeripheral      : MATSHITA DVD-RAM UJ-846S         atapi Port 0 ID 0  DMA: On 
DiskPeripheral       : WDC WD2500JS-98NCB1              atapi Port 1 ID 0  DMA: On 

=== CDRom-Device-Map ===
MATSHITA DVD-RAM UJ-846S   G:   CdRom0
=======================

AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 2038MB (2087020kB)
Free physical memory: 1564MB (1602028kB)
Memory in use       : 23 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

10.9.2008
CD-ROM (ISO)
4:14:57 PM	#1 Text 0 File SCSIPTICommands.cpp, Line 424
	LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	
4:14:57 PM	#2 Text 0 File Isodoc.cpp, Line 6666
	Iso document burn settings
	------------------------------------------
	Determine maximum speed : FALSE
	Simulate                : FALSE
	Write                   : TRUE
	Finalize CD             : FALSE
	Multisession            : TRUE
	Multisession type:      : Start multisession
	Burning mode            : TAO
	Mode                    : 1
	ISO Level               : 1 (Max. of 11 = 8 + 3 char)
	Character set           : ISO 9660
	Joliet                  : TRUE
	Allow pathdepth more than 8 directories : TRUE
	Allow more than 255 characters in path  : TRUE
	Write ISO9660 ;1 file extensions        : TRUE
	
4:14:57 PM	#3 Text 0 File Burncd.cpp, Line 3196
	MATSHITA DVD-RAM UJ-846S
	SmoothLink activated
	
4:14:57 PM	#4 ISO9660GEN -11 File Geniso.cpp, Line 3343
	First writeable address = 0 (0x00000000)
	
4:14:57 PM	#5 Text 0 File Burncd.cpp, Line 3508
	Turn on Track-At-Once, using CD-R/RW media
	
4:14:57 PM	#6 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:   359845 ( 79:59.70)
	Last address to be written:              86419 ( 19:14.19)
	
4:14:57 PM	#7 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO (enabled: CD)
	
4:14:57 PM	#8 Text 0 File DlgWaitCD.cpp, Line 2972
	Recorder: MATSHITA DVD-RAM UJ-846S;
	   CDR code: 00 97 26 66; OSJ entry from: CMC Magnetics Corporation
	   ATIP Data:
	     Special    Info [hex] 1: D0 00 98, 2: 61 1A 42 (LI 97:26.66), 3: 4F 3B 47 (LO 79:59.71)
	     Additional Info [hex] 1: 00 00 00 (invalid), 2: 00 00 00 (invalid), 3: 00 00 00 (invalid)
	
4:14:57 PM	#9 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
4:14:57 PM	#10 Text 0 File ThreadedTransferInterface.cpp, Line 793
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 ()
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 86420 (86420) = #86420/19:12.20
	    relocatable, disc pos for caching/writing not required/ required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 86418 blocks [G: MATSHITA DVD-RAM UJ-846S]
	--------------------------------------------------------------
	
4:14:57 PM	#11 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [G: MATSHITA DVD-RAM UJ-846S] for write in TAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc not fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0        307200     177295360, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	     -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	     -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |    86420 |        0 | 0x00
	    86420 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
4:14:57 PM	#12 Text 0 File ThreadedTransferInterface.cpp, Line 1066
	Removed 2 run-out blocks from end of track 1. Length: 86420 -> 86418.
	
4:14:57 PM	#13 Text 0 File SCSIPTICommands.cpp, Line 215
	SPTILockVolume - completed successfully for FSCTL_LOCK_VOLUME
	
4:14:58 PM	#14 Text 0 File Burncd.cpp, Line 4294
	Caching options: cache CDRom or Network-Yes, small files-No (<64KB)
	
4:14:58 PM	#15 Phase 24 File dlgbrnst.cpp, Line 1762
	Caching of files started
	
4:14:58 PM	#16 Text 0 File Burncd.cpp, Line 4413
	Cache writing successful.
	
4:14:58 PM	#17 Phase 25 File dlgbrnst.cpp, Line 1762
	Caching of files completed
	
4:14:58 PM	#18 Phase 36 File dlgbrnst.cpp, Line 1762
	Burn process started at 24x (3,600 KB/s)
	
4:14:58 PM	#19 Text 0 File ThreadedTransferInterface.cpp, Line 2721
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
4:14:58 PM	#20 Text 0 File MMC.cpp, Line 22363
	Set BUFE: SmoothLink -> ON 
	
4:14:58 PM	#21 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
4:16:56 PM	#22 Text 0 File MMC.cpp, Line 17131
	<MATSHITADVD-RAM UJ-846S > start Close Session

---

### Post by Yezinki on 2008-09-11
Solved issue..........changed Px2 engine to higher con fig.

Thanks!!

---

### Post by cyber_brain_mfkg on 2009-07-29
what is Px2 engine and how to configure it to work! i have same problem with same CD/DVD ROM...
thanx in advance!

---

### Post by claypole on 2009-11-22
Same here, any more info available?

---

### Post by claypole on 2009-11-22
Ok, I found the fix for my problem...

I had a nightmare with the "SK=3h/POWER CALIBRATION AREA ERROR" error on a LITE-ON LH-20A1H, trying to burn a 3Gb DVD ISO.

After much searching and no clear answer I found this link [http://codeguys.rpc1.org/firmwares.html](http://codeguys.rpc1.org/firmwares.html) through another forum related to this problem that enabled me to upgrade the firmware of my drive (using the .exe and WINE).

Now it all works fine and at the full 8X speed :guitar:

Hopefully this will help others with this very frustrating problem.

---

### Post by adijumi on 2010-04-06
I also occasionally get this error with no apparent reasons. Couple of times I tried burning that errored dvd R+ again with reduced file size (excluding spoiled amount) and it burned nicely. Go figure:guitar:

---

