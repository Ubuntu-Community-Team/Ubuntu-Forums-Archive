---
title: "What is happening in my CD burner?"
date: 2009-06-11
forum: Hardware
---

### Post by J-Morris on 2009-06-11
I am trying to use K3B to burn a cd on an external TDK brand CD writer. I get the following debugging output:

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-24-generic
Devices
-----------------------
TDK CDRW121032 1.02 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Text len: 5238
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'TDK     '
Identification : 'CDRW121032      '
Revision       : '1.02'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1190112 = 1162 KB
Drive DMA Speed: 5249 kB/s 29x CD 3x DVD
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   10 MB (01:01.08) no preemp swab copy
Track 02: audio   20 MB (02:02.08) no preemp swab copy
Track 03: audio   30 MB (03:03.06) no preemp swab copy
Track 04: audio   61 MB (06:06.06) no preemp swab copy
Track 05: audio   30 MB (03:03.06) no preemp swab copy
Track 06: audio   20 MB (02:02.08) no preemp swab copy
Track 07: audio   10 MB (01:01.08) no preemp swab copy
Track 08: audio   20 MB (02:02.08) no preemp swab copy
Track 09: audio   30 MB (03:03.06) no preemp swab copy
Track 10: audio   61 MB (06:06.06) no preemp swab copy
Track 11: audio   30 MB (03:03.06) no preemp swab copy
Track 12: audio   20 MB (02:02.08) no preemp swab copy
Track 13: audio   10 MB (01:01.08) no preemp swab copy
Track 14: audio   20 MB (02:02.08) no preemp swab copy
Track 15: audio   30 MB (03:03.06) no preemp swab copy
Track 16: audio   61 MB (06:06.01) no preemp swab copy
Track 17: audio   30 MB (03:03.06) no preemp swab copy
Track 18: audio   20 MB (02:02.08) no preemp swab copy
Track 19: audio   10 MB (01:01.08) no preemp swab copy
Track 20: audio   20 MB (02:02.08) no preemp swab copy
Track 21: audio   30 MB (03:03.06) no preemp swab copy
Total size:      585 MB (57:58.49) = 260887 sectors
Lout start:      585 MB (58:00/37) = 260887 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 98961
Starting to write CD/DVD at speed  12.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 2117 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 00 00 00 00 00 0A 00 00 00 00 00 00 00 00
Sense Key: 0x0 No Additional Sense, Segment 0
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.008s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:    6.693s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=12 -dao driveropts=burnfree textfile=/tmp/k3bTCskgb.dat -overburn -useinfo -audio /tmp/kde-j/k3b_audio_0_01.inf /tmp/kde-j/k3b_audio_0_02.inf /tmp/kde-j/k3b_audio_0_03.inf /tmp/kde-j/k3b_audio_0_04.inf /tmp/kde-j/k3b_audio_0_05.inf /tmp/kde-j/k3b_audio_0_06.inf /tmp/kde-j/k3b_audio_0_07.inf /tmp/kde-j/k3b_audio_0_08.inf /tmp/kde-j/k3b_audio_0_09.inf /tmp/kde-j/k3b_audio_0_10.inf /tmp/kde-j/k3b_audio_0_11.inf /tmp/kde-j/k3b_audio_0_12.inf /tmp/kde-j/k3b_audio_0_13.inf /tmp/kde-j/k3b_audio_0_14.inf /tmp/kde-j/k3b_audio_0_15.inf /tmp/kde-j/k3b_audio_0_16.inf /tmp/kde-j/k3b_audio_0_17.inf /tmp/kde-j/k3b_audio_0_18.inf /tmp/kde-j/k3b_audio_0_19.inf /tmp/kde-j/k3b_audio_0_20.inf /tmp/kde-j/k3b_audio_0_21.inf 


```

What should I do to get this burner working?

Thanks!

---

