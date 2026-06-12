---
title: "Prbolem installing new LG super multi DVD rewriter"
date: 2008-05-19
forum: Hardware
---

### Post by gilperzy on 2008-05-19
hi
I just got a new LG combo driver , GSA-H55L and Im having hard time installing it.

it doesnt read every cd , the ones he failed i mange to read in XP box, he does show me the content but when i try to run or copy a file it failes.

Another issue is that I can not manage to burn anything not a CD not a DVD; I tried gnomebaker , K3B and Nautilus.

this is a sample for the error I got
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type : Removable CD-ROM
Version : 5
Response Format: 2
Capabilities :
Vendor_info : 'HL-DT-ST'
Identification : 'DVD-RAM GSA-H55L'
Revision : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW)
Profile: 0x0016 (DVD-R/DL layer jump recording)
Profile: 0x0015 (DVD-R/DL sequential recording)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0011 (DVD-R sequential recording)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM)
Profile: 0x0002 (Removable disk)
Using generic SCSI-3/mmc CD-R/CD-RW driver (mmc_cdr).
Driver flags : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1114112 = 1088 KB
Drive DMA Speed: 124061 kB/s 704x CD 89x DVD
FIFO size : 12582912 = 12288 KB
Speed set to 2822 KB/s
 4 seconds. 3 seconds. 2 seconds. 1 seconds. 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 11700
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB: 2A 00 00 00 2D D3 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.003s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 63488 bytes
Writing time: 9.937s
Average write speed 395.1x.
Fixating...
Fixating time: 7.090s
wodim: fifo had 193 puts and 2 gets.
wodim: fifo was 0 times empty and 1 times full, min fill was 99%.


I will applicate any help

thank

---

