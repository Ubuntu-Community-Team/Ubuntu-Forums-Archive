---
title: "Easy Backup to cd/dvd Software"
date: 2008-11-09
forum: General Help
---

### Post by Rodney9 on 2008-11-09
Hello, I wish to back-up my photos everyday to a external hard drive and then to cd/dvd.

What is the easiest software to use that will be able to not copy the same photos over and over.

Rodney

---

### Post by Andreas1 on 2008-11-09
for backing up to the harddrive i always use **grsync**
it is a file synchronisation tool where you just set a local and a remote folder and then the remote folder is updatet to be identical to the local folder. look it up in synaptic.
i don't know if there is a way to do this with CDs as well, i never use them

---

### Post by Rodney9 on 2008-11-09
> **Andreas1 said:**
> for backing up to the harddrive i always use **grsync**
it is a file synchronisation tool where you just set a local and a remote folder and then the remote folder is updatet to be identical to the local folder. look it up in synaptic.
i don't know if there is a way to do this with CDs as well, i never use them

Thank You, Hopefully someone will know of a easy back-up to cd/dvd/hard drive software perfect for digital photos.

---

### Post by Rodney9 on 2008-11-09
Well i tried Pybackpack 0.5.5 but it continually fails with the follow message - 
> 
Mon Nov 10 11:14:43 2008: Starting backup of 'home' to CD

Mon Nov 10 11:14:43 2008: Analysing backup source.
Mon Nov 10 11:14:43 2008: Backup source analysis complete.
Mon Nov 10 11:14:43 2008: Creating temporary backup in /tmp
Mon Nov 10 11:15:08 2008: Creating CD image.
Mon Nov 10 11:15:08 2008: Backup failed; could not create CD image /tmp/pybackpack.iso

Any better easy back-up software for digital photos to cd/dvd/external-drive that works.

---

### Post by Rodney9 on 2008-11-09
I now have tried Simple Backup Config aswell as Pybackpack, they both fail, do any work ?

---

### Post by Rodney9 on 2008-11-10
I now have tried Simple Backup Config as well as Pybackpack, they both fail, do any work ?

---

### Post by Rodney9 on 2008-11-10
> **Rodney9 said:**
> I now have tried Simple Backup Config as well as Pybackpack, they both fail, do any work ?

So there is none ???

---

### Post by stinger30au on 2008-11-10
> **Rodney9 said:**
> Hello, I wish to back-up my photos everyday to a external hard drive and then to cd/dvd.

What is the easiest software to use that will be able to not copy the same photos over and over.

Rodney

for backup the external hdd i use syncback, you need to install wine first

wine
[http://www.winehq.org/](http://www.winehq.org/)

syncback freeware
[http://www.2brightsparks.com/downloads.html](http://www.2brightsparks.com/downloads.html)

for backup to dvd/cd i use wine and i use backup to cd made simple from willow soft , runs well in wine

[http://www.willowsoft.com/backup/index.html](http://www.willowsoft.com/backup/index.html)

---

### Post by Rodney9 on 2008-11-12
Everytime I try Grsync to backup to /cdrom/ it fails.

Is /cdrom/ the correct file for blank cd/dvd ?

---

### Post by Rodney9 on 2008-11-13
This message is what I get when trying to burn a cd, but nothing happens, the cd doesn't burn.

rodney@rodney-desktop:~$ cdrecord dev=/dev/cdrom driveropts=burnfree -v -data /home/rodney/Pictures/
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GH22NS30'
Revision       : '1.00'
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
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1114112 = 1088 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 126494 kB/s 718x CD 91x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data  unknown length
Total size:        0 MB (00:00.00) = 0 sectors
Lout start:        0 MB (00:02/00) = 0 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
wodim: WARNING: Total disk size unknown. Data may not fit on disk.
Speed set to 8468 KB/s
Starting to write CD/DVD at speed  48.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 MB written.wodim: Is a directory. read error on input file
Writing  time:    0.028s
wodim: fifo had 1 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

---

