---
title: "CD/DVD Burner Incompatibility"
date: 2011-12-02
forum: Hardware
---

### Post by lol_bear on 2011-12-02
First off I wanted to say thanks to everyone who made Ubuntu possible. It is in my opinion the best distro out there. I'm have a very nagging problem with my burner on my Lenovo Y560 it comes with a MATSHITA DVD-RAM UJ890 and I'm using 11.10 Ubuntu(all packages updated). However in every distro I've ran I've no matter ubuntu,kubuntu,xubuntu,opensuse, I get the same burning problems...pun intended.

For the record the error is completely random sometimes it will be buffer problems try using a different write speed, or on the next attempt it will be try using a different write mode.

I have gone through numerous discs to try to solve it and I think it lies somewhere linux's ability to calibrate the the proper power. I had no problems in windows (I hate windows) I do prosupport for Dell and I have to fix hundreds of cases with windows on a daily basis. So for my home laptop I use *buntu versions. Anyway I started getting a consistent debug log after I manually dropped the burn speed down to 4x, it says the burner doesnt support 4x and then bumps it up to 8x where it promptly fails at least I still just get one error message now. Full debug log below.

```
Devices
-----------------------
MATSHITA DVD-RAM UJ890 SB51 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.7.2 (4.7.2)
QT Version:  4.7.4
Kernel:      3.0.0-13-generic-pae

Used versions
-----------------------
cdrecord: 1.1.11

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ890   '
Revision       : 'SB51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 524288 = 512 KB
FIFO size      : 12582912 = 12288 KB
Encoding speed : 560x (41982 sectors/s) for libedc from Heiko Ei&#65533;feldt
Speed set to 1411 KB/s
Track 01: data   699 MB        
Total size:      803 MB (79:33.84) = 358038 sectors
Lout start:      803 MB (79:35/63) = 358038 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 1811
Starting to write CD/DVD at speed   8.0 in real RAW/RAW96R mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
/usr/bin/wodim: WARNING: Drive returns wrong startsec (0) using -11607 from ATIP
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF D3 C7 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 FF FF D2 B2 0A 00 13 00 00 10 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x10 Qual 0x00 (id crc or ecc error) Fru 0x0
Sense flags: Blk -11598 (valid) 
cmd finished after 0.003s timeout 40s
/usr/bin/wodim: Could not write Lead-in.
Writing lead-in at sector -11607
write leadin data: error after 700128 bytes
Writing  time:    4.132s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -raw96r driveropts=burnfree -data -tsize=358038s -
***********************
```
Also, I have tried running it as root, and I've set and set and reset the permissions to root. I'm using K3B, its the only one I can get to work when it does which is 1 out 50 times. I'm not even joking. I'm willing to admit I bought a cheap office depot brand of cdrs, but damnit I have two whole cake boxes I cant return. I doubt its the cdr's but lets try to fix this before I jump ship and say it is the cdrs, but I can retry on the same disc that failed to burn many times and then it will burn after many failed attempts. Confusing right? Anyway, for all of you Sherlocks out there this is a good one to figure out. Thanks for your help in advance. Edit** Don't know if it matters but Im using 32bit because I was told it was better supported than 64bit. If 64bit has the fix I will jumpship.

---

### Post by dandnsmith on 2011-12-02
Looks like you have a bug of some sort, or perhaps the drive firmware is in need of an update.
Your drive appears on the Ubuntu certified hardware lists - have a look at [this page](http://www.ubuntu.com/certification/catalog/component/scsi:1077C:10014-CDROM)

---

