---
title: "cdrecord permission problem Help"
date: 2008-11-03
forum: General Help
---

### Post by noppie on 2008-11-03
Ok I am running a desk top computer with a amd chip.sempron (something like that)  and I am trying to burn the 1so file for the next ubuntu 810.
I am trying to use the kb3
and I get the cdrecord permission problem
and I read the forums.. and do not understand what I am suppose to do.. I am using 8.04 (is that the last one before 8.10?) 
but I am totally lost on how to fix this.. below is the error.
Please I am begging someone to help me..
I need to burn the cd because I upgraded to 810 and am having problems with that (which in a different thread) 

Thank you for taking your time to read this.
Noppie:confused:


> -----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-15-generic
Devices
-----------------------
ATAPI CD-R/RW 8X4X32 5.CX (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, RAW/R16]

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
TOC Type: 1 = CD-ROM
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ATAPI   '
Identification : 'CD-R/RW 8X4X32  '
Revision       : '5.CX'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO RAW/R16
Drive buf size : 1634304 = 1596 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1434 KB/s
Track 01: data   698 MB        
Total size:      802 MB (79:30.61) = 357796 sectors
Lout start:      802 MB (79:32/46) = 357796 sectors
Current Secsize: 2048
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 2050
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  698 MB written.
Track 01:    1 of  698 MB written (fifo 100%) [buf  84%]   7.3x.
Track 01:    2 of  698 MB written (fifo 100%) [buf  97%]   0.2x.
Track 01:    3 of  698 MB written (fifo 100%) [buf  97%]   4.3x.
Track 01:    4 of  698 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    5 of  698 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    6 of  698 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    7 of  698 MB written (fifo 100%) [buf  96%]   4.1x.
Track 01:    8 of  698 MB written (fifo 100%) [buf  99%]   4.3x.
Track 01:    9 of  698 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   10 of  698 MB written (fifo 100%) [buf  98%]   4.0x.
Track 01:   11 of  698 MB written (fifo 100%) [buf  98%]   4.2x.
Track 01:   12 of  698 MB written (fifo 100%) [buf  97%]   4.0x.
Track 01:   13 of  698 MB written (fifo 100%) [buf  99%]   4.3x.
Track 01:   14 of  698 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   15 of  698 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   16 of  698 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:   17 of  698 MB written (fifo 100%) [buf  97%]   4.1x.
Track 01:   18 of  698 MB written (fifo 100%) [buf  97%]   4.0x.
Track 01:   19 of  698 MB written (fifo 100%) [buf  96%]   4.1x.
Track 01:   20 of  698 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:   21 of  698 MB written (fifo 100%) [buf  99%]   4.1x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 2A BF 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 38 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x38 Qual 0x00 (event status notification) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.380s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 18.661s timeout 200s
write track data: error after 22411264 bytes
Writing  time:  133.773s
Average write speed  35.7x.
Min drive buffer fill was 96%
Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.020s timeout 200s
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 200s
Trouble flushing the cache
Fixating time:   52.286s
/usr/bin/wodim: fifo had 545 puts and 354 gets.
/usr/bin/wodim: fifo was 0 times empty and 351 times full, min fill was 98%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=8 -dao -eject -data -tsize=357796s - 



---

### Post by SonicSteve on 2009-01-02
For those who come across this thread I had the same issue. 
I found that I needed to 
sudo chmod 777 /media/cdrom
I then did the same to /media/cdrom0 and /media/cdrom1 
these are the filesystem mount points that the cd/dvd drives use. 
I did everything I could think of to /dev/scd0 and /dev/scd1 but the device listings seemed to be fine. It seemed to be a permissions problem with the automount of CD/DVD

---

