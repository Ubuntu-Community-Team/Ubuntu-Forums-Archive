---
title: "CD-R Drive not working"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by risk on 2007-08-15
My cd-r drive can read cds but not burn them.. I'm trying to burn an iso using cd creator but it stalls for a few minutes and then produces an error message saying that I should try a smaller burn speed. I've tried every burn speed available but it still won't work! :confused:

I noticed 'is mounted 'and 'is writable' are false when listing the cddrives 

```

ryan@ryan-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:                 CW038D CD-R/RW
  device:               /dev/scd1
  door:                 closed
  type:                 CD-R, CD-RW, CD
  is mounted:           FALSE
  max read speed:       7060 KiB/s (CD 47.0x, DVD 5.2x)
  max write speed:      2824 KiB/s (CD 18.8x, DVD 2.0x)
  write speeds:         2700 KiB/s (CD 18.0x, DVD 1.9x)
                        2550 KiB/s (CD 17.0x, DVD 1.8x)
                        2400 KiB/s (CD 16.0x, DVD 1.7x)
                        2250 KiB/s (CD 15.0x, DVD 1.6x)
                        2100 KiB/s (CD 14.0x, DVD 1.5x)
                        1950 KiB/s (CD 13.0x, DVD 1.4x)
                        1800 KiB/s (CD 12.0x, DVD 1.3x)
                        1650 KiB/s (CD 11.0x, DVD 1.2x)
                        1500 KiB/s (CD 10.0x, DVD 1.1x)
                        1350 KiB/s (CD 9.0x, DVD 0.9x)
                        1200 KiB/s (CD 8.0x, DVD 0.8x)
                        1050 KiB/s (CD 7.0x, DVD 0.7x)
                        900 KiB/s (CD 6.0x, DVD 0.6x)
                        750 KiB/s (CD 5.0x, DVD 0.5x)
                        600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---
Drive:
  name:                 DVD-ROM 16X
  device:               /dev/scd0
  door:                 open
  type:                 CD, DVD
  is mounted:           FALSE
  max read speed:       2824 KiB/s (CD 18.8x, DVD 2.0x)
  max write speed:      0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:
Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---

```

---

### Post by risk on 2007-08-15
This is the k3b debug output

```

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
CyberDrv CW038D CD-R/RW 110C (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

IDE DVD-ROM 16X 1.32 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 64512
cmd finished after 431.689s timeout 200s
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'CyberDrv'
Identification : 'CW038D CD-R/RW  '
Revision       : '110C'
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
/usr/bin/wodim: Cannot eject media.
Track 01: data   579 MB        
Total size:      665 MB (65:53.45) = 296509 sectors
Lout start:      665 MB (65:55/34) = 296509 sectors

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=6 -dao driveropts=burnfree -eject -data -tsize=296509s - 


```

The drive doesn't even make any noise as though it is attempting to burn, it just sits idle!

---

### Post by dabl on 2007-08-15
In your output, I'm seeing some confusion about the designation of your CD drive as being either /dev/scd0 or /dev/scd1.  Probably /dev/scd0 is the right answer (you can check it in /etc/fstab).  Wish I could get more specific about what to do, but I think this is the essence of the problem.  Make sure that your mount point is mounting the correct device.

  :confused:

---

