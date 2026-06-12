---
title: "SATA DVD drive failing to burn"
date: 2010-02-27
forum: Hardware
---

### Post by talbain on 2010-02-27
I turned internet upside down without being able to find something specific regarding my problem.

I have recently purchased a LG HL-DT-ST DVDRAM GH22NS50 SATA DVD writer that doesnt seem to have a consistent behaviour when it comes to burning DVDs and im tired of burning coasters.

To complicate things further, i have a second SATA DVD writer on this machine that burns fine (PIONEER DVD-RW DVR-216D).

Im not sure if its got something to do with the motherboards BIOS version and SATA support or the firmware/chipset on the drive or its some kind of linux kernel incompatibility or maybe its some configuration problem?

I usually search and read a lot trying to fix as much as i can on my own, but this is really beyond me and forces me to ask for help.

Would anyone help me troubleshoot this?

This is K3B error output when trying to burn an image:

```

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-18-generic
Devices
-----------------------
HL-DT-ST DVDRAM GH22NS50 TN02 (/dev/sr1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

PIONEER DVD-RW  DVR-216D 1.08 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr1 obs=32k seek=0'
/dev/sr1: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=290h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-( write failed: Invalid argument
/dev/sr1: flushing cache
/dev/sr1: updating RMA
/dev/sr1: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr1=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2290284 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m

```This is the output of Gnomebaker:

```

Executing 'builtin_dd if=/media/disk/movie.iso of=/dev/sr1 obs=32k seek=0'
/dev/sr1: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=100h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-( write failed: Invalid argument
/dev/sr1: flushing cache
/dev/sr1: updating RMA
/dev/sr1: closing disc

```NeroLinux burns ok, but i'd like not to use it if possible, in part because id like to burn more than one disc at once provided i have two DVD writers.


$ cdrecord -scanbus

```

scsibus2:
    2,0,0    200) 'PIONEER ' 'DVD-RW  DVR-216D' '1.08' Removable CD-ROM
    2,1,0    201) *
    2,2,0    202) *
    2,3,0    203) *
    2,4,0    204) *
    2,5,0    205) *
    2,6,0    206) *
    2,7,0    207) *
scsibus3:
    3,0,0    300) 'HL-DT-ST' 'DVDRAM GH22NS50 ' 'TN02' Removable CD-ROM
    3,1,0    301) *
    3,2,0    302) *
    3,3,0    303) *
    3,4,0    304) *
    3,5,0    305) *
    3,6,0    306) *
    3,7,0    307) *

```$ cdrdao  drive-info

```

  Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

ERROR: Cannot open SCSI device '/dev/cdrw': Cannot open '/dev/cdrw'
Supported SCSI transports for this platform:

Transport name:        sg
Transport descr.:    Generic transport independent SCSI
Transp. layer ind.:    
Target specifier:    bus,target,lun
Target example:        1,2,0
SCSI Bus scanning:    supported
Open via UNIX device:    not supported

Transport name:        pg
Transport descr.:    SCSI transport for ATAPI over Parallel Port
Transp. layer ind.:    
Target specifier:    bus,target,lun
Target example:        1,2,0
SCSI Bus scanning:    supported
Open via UNIX device:    not supported

Transport name:        ATA
Transport descr.:    ATA Packet specific SCSI transport
Transp. layer ind.:    ATAPI:
Target specifier:    bus,target,lun
Target example:        ATAPI:1,2,0
SCSI Bus scanning:    supported
Open via UNIX device:    not supported

Transport name:        ATA
Transport descr.:    ATA Packet specific SCSI transport using sg interface
Transp. layer ind.:    ATA:
Target specifier:    bus,target,lun
Target example:        1,2,0
SCSI Bus scanning:    supported
Open via UNIX device:    not supported
ERROR: Please use option '--device [proto:]bus,id,lun', e.g. --device 0,6,0 or --device ATA:0,0,0
ERROR: Cannot setup device /dev/cdrw.

```$ hwinfo --cdrom

```

  25: SCSI 300.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50
  Unique ID: nOPI.jqdpvH78A08
  Parent ID: W60f.ccnC82JNK8E
  SysFS ID: /class/block/sr1
  SysFS BusID: 3:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.5/host3/target3:0:0/3:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVDRAM GH22NS50"
  Vendor: "HL-DT-ST"
  Device: "DVDRAM GH22NS50"
  Revision: "TN02"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr1 (/dev/sg3)
  Device Number: block 11:1 (char 21:3)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (IDE interface)
  Drive Speed: 48

26: SCSI 200.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_216D
  Unique ID: KD9E.r6eTSZfpRz1
  Parent ID: W60f.ccnC82JNK8E
  SysFS ID: /class/block/sr0
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.5/host2/target2:0:0/2:0:0:0
  Hardware Class: cdrom
  Model: "PIONEER DVD-RW  DVR-216D"
  Vendor: "PIONEER"
  Device: "DVD-RW  DVR-216D"
  Revision: "1.08"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr0 (/dev/sg2)
  Device Number: block 11:0 (char 21:2)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (IDE interface)
  Drive Speed: 12

```dmesg | grep DVD

```

[    3.504685] ata3.00: ATAPI: PIONEER DVD-RW  DVR-216D, 1.08, max UDMA/66
[    4.032185] ata4.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    4.087812] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-216D 1.08 PQ: 0 ANSI: 5
[    4.184660] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5

```$ sudo hdparm /dev/sr0

```

/dev/sr0:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```$ sudo hdparm /dev/sr1

```

/dev/sr1:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```EDIT: Changing SATA mode from AHCI to IDE in the BIOS made a difference, the system is overall more stable this way.

Im not sure what other info to provide, or where to look for anything else that may be related, will provide further if required. Thanks in advance.

---

### Post by talbain on 2010-02-28
Bump?

---

### Post by talbain on 2010-03-02
another bump?

---

### Post by broli on 2010-03-10
same problem here.

Also happns in fedora 11, fedora 12, and gentoo

---

### Post by betasam on 2010-03-17
Had the same problem. Tried with a custom compiled 2.6.33 kernel and the current git tree. It doesn't look like cdrkit is the source of the trouble. Drive Sense is going crazy after the cue sheet is written. Unable to write raw from the console as the drive spews out code that the driver can't interpret and userland programs don't get any further.

Is there a launchpad bug for this?

GH22NS50 is the model of the burner I got yesterday. The damn thing works on Windoze.

---

### Post by kriogenic on 2011-01-16
Hi, i have the same problem , my  Drive HL-DT-ST DVDRAM GH20NS15  :(   I go buying other DVD drive Not LG

---

