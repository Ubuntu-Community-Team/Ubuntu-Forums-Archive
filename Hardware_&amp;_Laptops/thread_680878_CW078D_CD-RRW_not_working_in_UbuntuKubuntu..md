---
title: "CW078D CD-R/RW not working in Ubuntu/Kubuntu."
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Crazywulf on 2008-01-28
Ok to make it short, for some reason I can't seem to burn discs with Ubuntu anymore.   I realize my drive isn't exactly name brand and is certainly generic, but I do remember I was able to burn at least once before.    I've tried logging in as root, tried pretty much every burner app out there and always end up getting a failed message.    Yesterday I even went so far as doing a clean install and trying to start from scratch, just in case I installed something that screwed up some settings.   Even with a fresh install it's not working.   Below I'm going to post the output log I get from k3b,  Can anyone give me any suggestions at all?    Thanks :)
----------------------------------------------------------------------------------

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
CyberDrv CW078D CD-R/RW 120D (/dev/hdb, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'CyberDrv'
Identification : 'CW078D CD-R/RW  '
Revision       : '120D'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
Drive DMA Speed: 358400 kB/s 2036x CD 258x DVD
FIFO size      : 12582912 = 12288 KB
resid: 4
resid: 2
resid: 4
resid: 2
/usr/bin/wodim: Warning: controller returns zero sized CD write parameter page.
/usr/bin/wodim: Warning: controller returns wrong size for CD write parameter page.
/usr/bin/wodim: Warning: controller returns wrong page 0 for CD write parameter page (5).
/usr/bin/wodim: Warning: controller returns zero sized CD write parameter page.
/usr/bin/wodim: Warning: controller returns wrong size for CD write parameter page.
/usr/bin/wodim: Warning: controller returns wrong page 0 for CD write parameter page (5).
/usr/bin/wodim: Cannot init drive.
Track 01: data   554 MB        
Total size:      636 MB (63:02.78) = 283709 sectors
Lout start:      636 MB (63:04/59) = 283709 sectors
Current Secsize: 1692766122
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdb speed=36 -dao driveropts=burnfree -overburn -data -tsize=283709s -

---

### Post by jeffus_il on 2008-01-28
Try another program other than k3b, gnomebaker, Brasero or just burn from Nautilus.

---

### Post by Crazywulf on 2008-01-28
As I've said, I've tried all of these.   All of them give me a failed message.    I posted the k3b output because some don't give the output to look at and simply say *failed*.     I should also point out that in k3b, the first time I'm about to burn the image it shows the blank disc medium properly.    IF I close out completly and restart k3b, it will say no cd-rw drive is detected.   If I open up the tray and take out the cd, the "blank cd-r" icon will stay on my desktop until I reset/logoff.

---

### Post by Crazywulf on 2008-01-28
[IMG]http://img225.imageshack.us/img225/5262/hmmmmcw2.jpg[/IMG]

I'd say unless my drive is from about 50yrs in the future, something is wrong.

---

### Post by jeffus_il on 2008-01-28
How does the kernel see it, use dmesg and maybe post the relevant lines.

---

### Post by Arkore on 2008-04-15
Hi, got the same problem with this drive.

It builds the ISO to burn then the moment it tries to send data to the drive the whole system hangs to the point where you have to slowly move the mouse to the cancel button because it only moves once every 5 seconds or so.  System recovers once the disk is removed from the drive.

Results from dmesg are as follows:

[64625.557592] cdrom: This disc doesn't have any tracks I recognize!
[65348.856098] hda: status timeout: status=0xd0 { Busy }
[65348.856108] ide: failed opcode was: unknown
[65348.856113] hda: drive not ready for command
[65353.883854] hda: status timeout: status=0xd0 { Busy }
[65353.883862] ide: failed opcode was: unknown
[65353.883867] hda: drive not ready for command
[65358.967562] hda: status timeout: status=0xd0 { Busy }
[65358.967572] ide: failed opcode was: unknown
[65358.967578] hda: drive not ready for command

etc......  I assume where it stopped repeating was when I canceled the operation.

Anyone got any ideas or should I just buy a new drive?

---

### Post by Arkore on 2008-04-15
Additional data that may help:

hdparm /dev/hda

/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

---

### Post by Arkore on 2008-04-15
As my reading takes me further I have new commands that give more info regarding the current state of the drive:


 hdparm -i /dev/hda

/dev/hda:

 Model=CW078D ATAPI CD-R/RW, FwRev=V120D, SerialNo=NC000000Q0
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4

 * signifies the current active mode


cdrecord -dev=ATAPI -scanbus
scsibus0:
        0,0,0     0) 'CyberDrv' 'CW078D CD-R/RW  ' '120D' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *


cat /proc/ide/hda/driver
ide-cdrom version 4.61


sudo hdparm -tT /dev/hda

/dev/hda:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error
BLKFLSBUF failed: Function not implemented


grep hda /etc/fstab
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by lupa18 on 2008-07-18
I have the same problem... please help us:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-18-generic
Devices
-----------------------
UNKNOWN ATAPI CDROM 100P (/dev/scd0, ) [CD-ROM] [Error] [Ninguno]

CyberDrv CW078D CD-R/RW 130D (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]
Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 337.180s timeout 200s
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'CyberDrv'
Identification : 'CW078D CD-R/RW  '
Revision       : '130D'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 12582912 = 12288 KB
/usr/bin/wodim: Cannot load media.
Track 01: data   680 MB        
Total size:      780 MB (77:22.40) = 348180 sectors
Lout start:      781 MB (77:24/30) = 348180 sectors

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=40 -dao driveropts=burnfree -overburn -data -tsize=348180s -

---

