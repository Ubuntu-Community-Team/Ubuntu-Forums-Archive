---
title: "DVD drive vs. Ubuntu"
date: 2009-04-21
forum: Hardware
---

### Post by woollypigs on 2009-04-21
My DVD drive  on my Sony SZ2XP is a combo CD/DVD/read/writey thingie (MATSHITA UJ-832D) but since I have started to use Ubuntu the DVD part has been a no go area. I have been using Ubuntu since 6.04, and I think at the start it was reading the DVD's just fine , I'm now trying out 9.04 beta and have just updated everything including the codecs.

Not really been a problem before but now I need to copy a DVD and also would like to just view a DVD.

As I up till now I only have needed the CD-RW part of the drive. When I was using XP the DVD part worked just fine, and in Virtualbox, XP sees the drive as a DVD-R but I get an I/O error when putting a DVD movie in.

I have search the www and have just hit dead ends, anyone here got an idea where to look to fix this problem ?

> sudo cdrecord -scanbus :
scsibus0:
   0,0,0     0) 'MATSHITA' 'UJ-832D         ' '1.70' Removable CD-ROM
   0,1,0     1) *
   0,2,0     2) *
   0,3,0     3) *
   0,4,0     4) *
   0,5,0     5) *
   0,6,0     6) *
   0,7,0     7) *


> 
sudo lshw

 *-cdrom
                description: DVD writer
                product: UJ-832D
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.70
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom


> 
sudo cdrecord -atip (without a disk)

Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'MATSHITA'
Identification : 'UJ-832D         '
Revision       : '1.70'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
wodim: Cannot load media.


So Ubuntu is seeing it as a DVD drive but still don't play the DVD.

---

### Post by woollypigs on 2009-04-28
bump 

Anyone got an idea ?

---

### Post by lisati on 2009-04-28
Which version of Ubuntu are you using? For help with DVDs on the latest (9.04), have a look here: [https://help.ubuntu.com/9.04/musicvideophotos/C/video.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video.html)

---

### Post by woollypigs on 2009-04-30
Running 9.04 all up to date. 

Just followed your link, got everything there already.

I think the main reason it is not working is that Ubuntu is not mounting the DVD at all therefore no program will read the drive.

---

### Post by bemar on 2012-11-25
I have also a matshita dvd drive and exactly the same error.
Seems to be this drives are bulshit.

Ben

---

