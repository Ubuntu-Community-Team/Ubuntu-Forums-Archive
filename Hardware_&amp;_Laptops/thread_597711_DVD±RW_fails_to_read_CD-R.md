---
title: "DVD±RW fails to read CD-R"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by lduplantie on 2007-10-30
I recently installed Ubuntu 7.10 and noticed that my Pioneer DVR-112D DVD±RW cannot read (or even mount) CD-ROMs (pre-recorded or burnt under Windows XP). I know the drive is capable of reading or recording CDs. 

Here is the output of cdrecord -scanbus:

Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
scsibus0:
        0,0,0     0) 'ATA     ' 'IC35L020AVER07-0' 'ER2O' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus1:
        1,0,0   100) 'SAMSUNG ' 'CD-ROM SC-148C  ' 'B100' Removable CD-ROM
        1,1,0   101) 'PIONEER ' 'DVD-RW  DVR-112D' '1.09' Removable CD-ROM
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

Output of: cdrecord dev=1,1,0 -checkdrive
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
scsidev: '1,1,0'
scsibus: 1 target: 1 lun: 0
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-112D'
Revision       : '1.09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP

The command eject /dev/scd1 (-t) will open (close) the DVD tray 
The command eject /dev/scd0 (-t) will open (close) the CD-R tray

I can mount a data dvd in the dvd drive, but cannot mount a CD-R.
I can mount the CD-R, tried in the DVD drive, in the CD-ROM drive.

Can you please help making the DVD drive read CD-ROM or record CDs

Thanks

---

### Post by ubuntu27 on 2007-11-11
Hello lduplantie :)

Can you post how you managed to solve your problem with details? ;)
That way other people will be able to solve their problems if the encounter the same symptoms.

---

### Post by lduplantie on 2007-11-11
Steps to problem resolution:

1: Verified that the problem was repeatable with many types of media:
    DVD-data, DVD-movie, CD-data (commercial and burned on a Win XP PC)
2: Posted on the Ubuntu Forum for assistance interpreting "dmesg" and 
    "cdrecord -scanbus". Installed K3B to verify it the drive was detected and could burn.
    CDs could still not be mounted. K3B would detect a blank CD or DVD.
    It would not burn a CD. K3B indicated that the media could be "bad".
3: Upgraded the device firmware. For this, I had to install the device in a Windows PC.
4: Verified if the same problem was present when the device was installed in the Windows
    PC. The problem was present with the exact same behavior. Clearly this meant that the
    device was at fault.
5: Purchased a new DVD±RW and installed in Ubuntu PC (i386).
6: Verified if the new device could mount CDs & DVDs - Yes
7: Burned a CD: Success!

I hope this will help anyone with a similar problem.

---

