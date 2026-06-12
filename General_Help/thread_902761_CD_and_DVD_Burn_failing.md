---
title: "CD and DVD Burn failing"
date: 2008-08-27
forum: General Help
---

### Post by gardara on 2008-08-27
I have a couple of burning issues on my ubuntu system...

First of all, burning data CD's fails sometimes and sometimes not... And when I burn data DVD's it always fails... What I am trying to burn are different .avi videos... I have tried brasero, nero and the inbuilt feature in ubuntu... Well The burn shows as successful in all of the applications but when I try to open the disc it does appear like there is no disc in the drive, and in nero, data verification fails.
The only program I have managed to get a error log is nero, and here it is:

```
2CA0-0000-1800-2000-4001-7834-****

Linux 2.6.24-19-server
Nero API version: 7.20.4.0
Using interface version: 7.5.1.2
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 20, 4, 0

Recorder:             <TSSTcorp DVD+-RW TS-L632D>Version: DE03 - HA 1 TA 0 - 0.0.0.0
 Adapter driver:      <ata_piix>                HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 3287MB (3366476kB)
Free physical memory: 119MB (122704kB)
Memory in use       : 96 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

23.8.2008
NeroAPI
19:28:32	#1 ISO9660GEN -11 File Geniso.cpp, Line 3350
	First writeable address = 0 (0x00000000)
	
19:28:32	#2 Text 0 File Burncd.cpp, Line 3549
	Turn on Disc-At-Once, using DVD media
	
19:28:33	#3 Text 0 File FilesystemSettingsValidator.cpp, Line 139
	FS Settings: using validator 'CUDFSettingsValidatorDVD'
	ParamMode = 'manual', changing UDF partition type from 'physical' to 'physical'
	Changing UDF revision from '1.02' to '1.02'
	
19:28:34	#4 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2295103 (510:01.28, 4482MB)
	Last address to be written:            1963247 (436:16.47, 3834MB)
	
19:28:34	#5 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
19:28:35	#6 Text 0 File DlgWaitCD.cpp, Line 2989
	Recorder: TSSTcorp DVD+-RW TS-L632D, Media type: DVD+R
	 Disc Manufacturer ID: <MCC>, Media Type ID: <004>, Product revision number: 0
	 Disc Application Code: 0, Extended Information Indicators: 7
	
19:28:35	#7 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
19:28:35	#8 Text 0 File ThreadedTransferInterface.cpp, Line 785
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 ()
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 1963248 (1963248) = #1963248/436:16.48
	    relocatable, disc pos for caching/writing not required/ required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 1963248 blocks [TSSTcorp DVD+-RW TS-L632D (H:1 T:0)]
	--------------------------------------------------------------
	
19:28:35	#9 Text 0 File ThreadedTransferInterface.cpp, Line 986
	Prepare [TSSTcorp DVD+-RW TS-L632D (H:1 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    4020731904, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  1963248 |        0 | 0x00
	  1963248 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
19:28:35	#10 Text 0 File Burncd.cpp, Line 4340
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
19:28:35	#11 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
19:28:35	#12 Text 0 File Burncd.cpp, Line 4459
	Cache writing successful.
	
19:28:35	#13 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
19:28:35	#14 Phase 28 File ExtendedProgress.cpp, Line 537
	Speed measurement started
	
19:28:36	#15 Text 0 File ThreadedTransferInterface.cpp, Line 2733
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
19:28:36	#16 Text 0 File ThreadedTransfer.cpp, Line 268
	Pipe memory size 590400
	
19:29:40	#17 Text 0 File WriterStatus.cpp, Line 240
	<TSSTcorp DVD+-RW TS-L632D (H:1 T:0)> start writing Lead-Out at LBA 1963248 (1DF4F0h), length 0 blocks
	
19:29:40	#18 Phase 29 File ExtendedProgress.cpp, Line 470
	Speed measurement completed: 44.5x (61422 KB/s)
	
19:29:40	#19 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 2.4x (3324 KB/s)
	
19:29:43	#20 Text 0 File ThreadedTransferInterface.cpp, Line 2733
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
19:29:43	#21 Text 0 File Cdrdrv.cpp, Line 10162
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD+R (10), Part Version: 1.0x (1)
	 Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Physical Sector Number of Data Area:          26053F h
	 Data in Burst Cutting Area (BCA) does not exist
	  Disc Application Code: 0 / 0 h
	  Extended Information indicators: 7 h
	  Disc Manufacturer ID: MCC.....
	  Media type ID: 004
	  Product revision number: 0
	  Number of Physical format information bytes in use in ADIP up to byte 63: 56
	 Media Specific [16..783]:
	    00 00 07 4D 43 43 00 00 - 00 00 00 30 30 34 00 38    ...MCC.....004.8
	    23 54 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    #T..............
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
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
19:29:43	#22 Text 0 File Cdrdrv.cpp, Line 10162
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD+R (10), Part Version: 1.0x (1)
	 Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Physical Sector Number of Data Area:          26053F h
	 Data in Burst Cutting Area (BCA) does not exist
	  Disc Application Code: 0 / 0 h
	  Extended Information indicators: 7 h
	  Disc Manufacturer ID: MCC.....
	  Media type ID: 004
	  Product revision number: 0
	  Number of Physical format information bytes in use in ADIP up to byte 63: 56
	 Media Specific [16..783]:
	    00 00 07 4D 43 43 00 00 - 00 00 00 30 30 34 00 38    ...MCC.....004.8
	    23 54 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    #T..............
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
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
19:29:43	#23 Text 0 File Cdrdrv.cpp, Line 10162
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD+R (10), Part Version: 1.0x (1)
	 Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Physical Sector Number of Data Area:          26053F h
	 Data in Burst Cutting Area (BCA) does not exist
	  Disc Application Code: 0 / 0 h
	  Extended Information indicators: 7 h
	  Disc Manufacturer ID: MCC.....
	  Media type ID: 004
	  Product revision number: 0
	  Number of Physical format information bytes in use in ADIP up to byte 63: 56
	 Media Specific [16..783]:
	    00 00 07 4D 43 43 00 00 - 00 00 00 30 30 34 00 38    ...MCC.....004.8
	    23 54 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    #T..............
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
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
19:29:43	#24 Text 0 File DVDR.cpp, Line 8366
	Drive: TSSTcorp DVD+-RW TS-L632D
	Book Type request [TSST]: DVD-ROM
	Changing the Book Type was finished successfully, return code 0
	
19:29:43	#25 CDR -1211 File DVDR.cpp, Line 6546
	Book Type set to: DVD-ROM
	
19:29:43	#26 Text 0 File DVDPlusRW.cpp, Line 675
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
19:29:43	#27 Text 0 File ThreadedTransfer.cpp, Line 268
	Pipe memory size 83836800
	
19:50:03	#28 Text 0 File WriterStatus.cpp, Line 240
	<TSSTcorp DVD+-RW TS-L632D (H:1 T:0)> start writing Lead-Out at LBA 1963248 (1DF4F0h), length 0 blocks
	
19:50:39	#29 Text 0 File DVDPlusRW.cpp, Line 935
	EndDAO: Last written address 1963248
	
19:50:39	#30 Phase 37 File ExtendedProgress.cpp, Line 537
	Burn process completed successfully at 2.4x (3324 KB/s)
	
19:50:39	#31 Phase 78 File ExtendedProgress.cpp, Line 537
	Data verification started
	
19:50:42	#32 Text 0 File ThreadedTransfer.cpp, Line 268
	Pipe memory size 590400
	
19:51:00	#33 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:51:08	#34 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x10 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:51:25	#35 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x20 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:51:34	#36 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x30 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:51:51	#37 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x40 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:51:59	#38 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x50 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:52:16	#39 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x60 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:52:25	#40 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x70 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:52:42	#41 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x80 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:52:50	#42 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0x90 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:53:07	#43 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0xA0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:53:16	#44 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0xB0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:53:33	#45 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0xC0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:53:41	#46 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0xD0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:53:58	#47 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0xE0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:54:07	#48 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x00 0xF0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:54:24	#49 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x00 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:54:33	#50 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x10 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:54:50	#51 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x20 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:54:58	#52 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x30 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:55:15	#53 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x40 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:55:24	#54 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x50 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:55:41	#55 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x60 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:55:49	#56 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x70 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:56:06	#57 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x80 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:56:15	#58 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0x90 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:56:32	#59 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0xA0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:56:40	#60 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0xB0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:56:57	#61 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0xC0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:57:06	#62 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0xD0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:57:23	#63 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0xE0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:57:31	#64 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x01 0xF0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:57:48	#65 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x00 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:57:57	#66 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x10 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:58:14	#67 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x20 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:58:22	#68 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x30 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:58:40	#69 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x40 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:58:48	#70 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x50 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:59:05	#71 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x60 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:59:14	#72 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xabc8f340
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x70 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:59:31	#73 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1b9800
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x80 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:59:39	#74 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1b9800
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0x90 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
19:59:56	#75 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb043b2c0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0xA0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:00:05	#76 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb043b2c0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0xB0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:00:22	#77 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb043b2c0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0xC0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:00:30	#78 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb043b2c0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0xD0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:00:47	#79 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0xE0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:00:56	#80 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x02 0xF0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:01:13	#81 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x00 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:01:21	#82 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x10 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:01:38	#83 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x20 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:01:47	#84 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x30 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:02:04	#85 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x40 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:02:12	#86 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x50 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:02:29	#87 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x60 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:02:38	#88 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x70 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:02:55	#89 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x80 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:03:04	#90 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0x90 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:03:21	#91 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0xA0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:03:29	#92 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0xB0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:03:46	#93 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0xC0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:03:55	#94 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0xD0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:04:12	#95 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0xE0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:04:20	#96 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x03 0xF0 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:04:37	#97 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x04 0x00 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:04:46	#98 SCSI -400 File SCSIInterface.cpp, Line 623
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb1f3000
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x04 (0x02, SCSI_TASTATUS_CONDMET)
	Sense Key:  0x04 (KEY_HARDWARE_ERROR)
	Sense Code: 0x3E
	Sense Qual: 0x02
	CDB Data:   0x28 0x00 0x00 0x00 0x04 0x10 0x00 0x00 0x10 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x3E 0x02 
	
20:04:46	#99 SectorVerify 20 File Cdrdrv.cpp, Line 11362
	Read errors from sector 0 to 1055
	
20:04:46	#100 CDR -1222 File Writer.cpp, Line 203
	Verification aborted, too much errors
	TSSTcorp DVD+-RW TS-L632D (H:1 T:0)
	
20:04:46	#101 Phase 81 File ExtendedProgress.cpp, Line 537
	Data verification failed
	
```

Second problem is when burning a iso to a disc... It shows as completed with the inbuilt burning program and nero, but nero verification fails and gives a error log... I can paste it here if needed.

Third problem is with burning audio cd's, nero, brasero and the inbuilt writer all fail to write audio cd's properly.. 

Those are probably all the same problem but I thought I should write about it all just in case...

As I said.. The only thing that doesn't fail all the time is when burning data cd...
I had a dual boot with windows that I recently got rid of, but I was able to burn discs successfully there....

I hope someone can help, I really need this working!

---

### Post by phidia on 2008-08-27
Are the avi files encrypted? When I googled this line "Data in Burst Cutting Area (BCA) does not exist" I got a lot of hits but perhaps most (?) relevent was [this]("http://www.osta.org/technology/dvdqa/dvdqa7.htm").

I don't know why you are not able to burn data through your optical drive though.
Perhaps this will sound too geeky but often using the CLI tools to burn with (either wodim or cdrecord) will give you more output/feedback. 
There's a lot of reading involved but try man wodim it can be helpful.

---

### Post by gardara on 2008-08-27
Thanks for the reply...

> **phidia said:**
> Are the avi files encrypted? When I googled this line "Data in Burst Cutting Area (BCA) does not exist" I got a lot of hits but perhaps most (?) relevent was [this]("http://www.osta.org/technology/dvdqa/dvdqa7.htm").


Yes and no.. I have no avi files that are encrypted themself.. But I do have tried to burn some files that I have on a truecrypt encrypted drive, and also files that have never been on that drive.. Both ways I get the same error...

> **phidia said:**
> I don't know why you are not able to burn data through your optical drive though.
Perhaps this will sound too geeky but often using the CLI tools to burn with (either wodim or cdrecord) will give you more output/feedback. 
There's a lot of reading involved but try man wodim it can be helpful.

I could try that... I thought it wouldn't matter tho... Since I have tried 3 different gui applications, and even tried straight after a reboot with no other applications open (In case some application was conflicting with the burning app)

---

### Post by phidia on 2008-08-27
> **gardara said:**
> Thanks for the reply...



Yes and no.. I have no avi files that are encrypted themself.. But I do have tried to burn some files that I have on a truecrypt encrypted drive, and also files that have never been on that drive.. Both ways I get the same error...



I could try that... I thought it wouldn't matter tho... Since I have tried 3 different gui applications, and even tried straight after a reboot with no other applications open (In case some application was conflicting with the burning app)

I can't agree with your last statement. The CLI burning tools have more flexibility and power than the gui burning tools. I just burnt a 715MB iso image using wodim with the overburn flag and some other commands and I can not do that with any of the available linux gui burning apps.

---

### Post by gardara on 2008-08-27
Oh really... Sounds interesting... I'll try a CLI burning tool and report back how it goes :)

---

