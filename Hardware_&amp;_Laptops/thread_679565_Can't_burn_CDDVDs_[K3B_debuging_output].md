---
title: "Can't burn CD/DVDs [K3B debuging output]"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by IamAcoconut on 2008-01-27
Nor can I erase a CD-/DVD-RW, as I just tried. Here's what K3b told me:
```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
QSI DVD+-RW SDW-082S LX06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R sekwencyjna, DVD-RW w trybie ograniczonego zast&#281;powania, DVD-RW sekwencyjny, DVD+RW, DVD+R, DVD+R dwuwarstwowa, CD-ROM, CD-R, CD-RW] [Sesja naraz (SAO), TAO, RAW, SAO/R96R, Surowe/R16, Surowe/R96R, Ograniczone zast&#281;powanie]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.

scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... giving up.
/usr/bin/wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
TOC Type: 1 = CD-ROM

```

I googled for a similar error output, and I found this: [http://www.mycity.co.yu/Linux-aplikacije/k3b-ne-brishe-rw-RESENO.html](http://www.mycity.co.yu/Linux-aplikacije/k3b-ne-brishe-rw-RESENO.html)
Do I need to have a cdrom entry in **/etc/fstab**? What should it look like? I'm running Ubuntu on an encrypted filesystem if that makes any difference.

PS. I did happen to run into problems with cd-burning from time to time, but most of the time it worked ok. Didn't install any update since the day before yesterday, when I had recorded a valid CD from an iso image. Now I can't do this.

---

### Post by IamAcoconut on 2008-01-31
**wodim -scanbus** and **wodim --devices** give me the same output```

wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```
Although I remember running these commands before and it was different :(

Now I've succesfully recorded an ISO image, though when trying to burn another CD i get:
```

(...)
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
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082S'
Revision       : 'LX06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 4234 KB/s
Track 01: data   631 MB        
Total size:      724 MB (71:48.45) = 323134 sectors
Lout start:      725 MB (71:50/34) = 323134 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 0
  Reference speed: 0
  Is not unrestricted
  Is erasable
  Disk sub type: Ultra High speed+ Rewritable media (3)
  ATIP start of lead in:  -11075 (97:34/25)
  ATIP start of lead out: 359849 (79:59/74)
  2T speed low:  8 2T speed high: 24
  power mult factor: 0 0
  recommended erase/write power: 0
  A1 values: 00 00 80
  A2 values: 38 80 00
  A3 values: 04 C4 B8
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359851 Blocks current: 359851 Blocks remaining: 36717
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0B 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  631 MB written.
Track 01:    1 of  631 MB written (fifo 100%) [buf  87%]   4.5x.
Track 01:    2 of  631 MB written (fifo 100%) [buf  87%]  10.4x.
Track 01:    3 of  631 MB written (fifo 100%) [buf  90%]  10.5x.
Track 01:    4 of  631 MB written (fifo 100%) [buf  90%]  10.7x.
Track 01:    5 of  631 MB written (fifo  99%) [buf  93%]  11.0x.
Track 01:    6 of  631 MB written (fifo 100%) [buf  90%]  10.3x.
Track 01:    7 of  631 MB written (fifo  99%) [buf  93%]  10.8x.
Track 01:    8 of  631 MB written (fifo  99%) [buf  93%]  10.1x.
Track 01:    9 of  631 MB written (fifo 100%) [buf  87%]   9.9x.
Track 01:   10 of  631 MB written (fifo 100%) [buf  87%]  10.2x.
Track 01:   11 of  631 MB written (fifo 100%) [buf  90%]  10.9x.
Track 01:   12 of  631 MB written (fifo 100%) [buf  90%]  10.0x.
Track 01:   13 of  631 MB written (fifo  99%) [buf  93%]  10.7x.
Track 01:   14 of  631 MB written (fifo  99%) [buf  93%]  10.0x.
Track 01:   15 of  631 MB written (fifo 100%) [buf  87%]   9.8x.
Track 01:   16 of  631 MB written (fifo 100%) [buf  87%]  10.1x.
Track 01:   17 of  631 MB written (fifo 100%) [buf  90%]  10.8x.
Track 01:   18 of  631 MB written (fifo 100%) [buf  90%]  10.0x.
Track 01:   19 of  631 MB written (fifo  99%) [buf  93%]  10.6x.
Track 01:   20 of  631 MB written (fifo  99%) [buf  93%]  10.0x.
Track 01:   21 of  631 MB written (fifo 100%) [buf  87%]   9.7x.
Track 01:   22 of  631 MB written (fifo 100%) [buf  87%]  10.0x.
Track 01:   23 of  631 MB written (fifo 100%) [buf  90%]  10.7x.
Track 01:   24 of  631 MB written (fifo 100%) [buf  90%]  10.0x.
Track 01:   25 of  631 MB written (fifo  99%) [buf  93%]  10.5x.
Track 01:   26 of  631 MB written (fifo 100%) [buf  93%]   9.9x.
Track 01:   27 of  631 MB written (fifo 100%) [buf  87%]   9.7x.
Track 01:   28 of  631 MB written (fifo 100%) [buf  87%]   9.9x.
Track 01:   29 of  631 MB written (fifo 100%) [buf  90%]  10.6x.
Track 01:   30 of  631 MB written (fifo 100%) [buf  90%]  10.0x.
Track 01:   31 of  631 MB written (fifo  99%) [buf  93%]  10.6x.
Track 01:   32 of  631 MB written (fifo  99%) [buf  93%]   9.9x.
Track 01:   33 of  631 MB written (fifo  99%) [buf  93%]  10.1x.
Track 01:   34 of  631 MB written (fifo 100%) [buf  87%]   9.9x.
Track 01:   35 of  631 MB written (fifo 100%) [buf  96%]  11.1x.
Track 01:   36 of  631 MB written (fifo 100%) [buf  90%]   9.9x.
Track 01:   37 of  631 MB written (fifo 100%) [buf  87%]  10.2x.
Track 01:   38 of  631 MB written (fifo 100%) [buf  90%]  10.9x.
Track 01:   39 of  631 MB written (fifo 100%) [buf  90%]  10.2x.
Track 01:   40 of  631 MB written (fifo 100%) [buf  93%]  10.8x.
Track 01:   41 of  631 MB written (fifo  99%) [buf  93%]  10.1x.
Track 01:   42 of  631 MB written (fifo 100%) [buf  87%]   9.8x.
Track 01:   43 of  631 MB written (fifo 100%) [buf  87%]  10.1x.
Track 01:   44 of  631 MB written (fifo 100%) [buf  90%]  10.8x.
Track 01:   45 of  631 MB written (fifo 100%) [buf  90%]  10.1x.
Track 01:   46 of  631 MB written (fifo  99%) [buf  93%]  10.8x.
Track 01:   47 of  631 MB written (fifo  99%) [buf  93%]  10.1x.
Track 01:   48 of  631 MB written (fifo 100%) [buf  87%]   9.7x.
Track 01:   49 of  631 MB written (fifo 100%) [buf  87%]  10.0x.
Track 01:   50 of  631 MB written (fifo 100%) [buf  90%]  10.7x.
Track 01:   51 of  631 MB written (fifo 100%) [buf  90%]  10.0x.
Track 01:   52 of  631 MB written (fifo  99%) [buf  93%]  10.6x.
Track 01:   53 of  631 MB written (fifo 100%) [buf  93%]  10.0x.
Track 01:   54 of  631 MB written (fifo 100%) [buf  87%]   9.8x.
Track 01:   55 of  631 MB written (fifo 100%) [buf  87%]  10.0x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 6E 70 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium 
cmd finished after 0.644s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 57901056 bytes
Writing  time:   47.117s
Average write speed  94.8x.
Min drive buffer fill was 87%
Fixating...
Fixating time:    3.307s
/usr/bin/wodim: fifo had 1104 puts and 913 gets.
/usr/bin/wodim: fifo was 0 times empty and 641 times full, min fill was 95%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -dao driveropts=burnfree -eject -data -tsize=323134s - 
```

---

