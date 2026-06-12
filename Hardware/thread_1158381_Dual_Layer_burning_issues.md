---
title: "Dual Layer burning issues"
date: 2009-05-13
forum: Hardware
---

### Post by Ghost Dog on 2009-05-13
I have a couple large .ISO's and DVD's I would like to burn, they are under 8GB's but are larger than 4GBs.  I have a dual layer burner, I tried burning them with K9 and the Brasero Disc Burner apps.  It seems to error out the instant it trys to burn the data to disc, it doesn't write anything because the disc is still recognized as a blank.  Here are some error codes it gives me.

Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 22 42 DC 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 12 00 00 00 00 72 01 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x72 Qual 0x01 (session fixation error writing lead-in) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 9.217s timeout 200s
wodim: Cannot open new session.

Thanks for any tips on this! I bought some dual layer DVD+r's I would like to use :)

---

### Post by Ghost Dog on 2009-05-13
Bump

---

### Post by Ghost Dog on 2009-05-20
so I tried K3B but I still get an error...this time it actually wrote something on the DL-DVD

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
DVDR/RW DD1601 15AF (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

ATAPI DVD DUAL 8X4X12 ATC1 (/dev/sr1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]
Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
:-? L0 Data Zone Capacity is set already
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
          0/8147599360 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    5373952/8147599360 ( 0.1%) @1.2x, remaining 227:16 RBU 100.0% UBU   4.8%
   15499264/8147599360 ( 0.2%) @2.2x, remaining 113:40 RBU 100.0% UBU  85.7%
   26509312/8147599360 ( 0.3%) @2.4x, remaining 81:41 RBU 100.0% UBU  85.7%
   37519360/8147599360 ( 0.5%) @2.4x, remaining 68:26 RBU 100.0% UBU  85.7%
   48627712/8147599360 ( 0.6%) @2.4x, remaining 63:50 RBU 100.0% UBU  85.7%
   58654720/8147599360 ( 0.7%) @2.2x, remaining 59:45 RBU 100.0% UBU  85.7%
   69664768/8147599360 ( 0.9%) @2.4x, remaining 56:02 RBU 100.0% UBU  85.7%
   80674816/8147599360 ( 1.0%) @2.4x, remaining 54:59 RBU 100.0% UBU  85.7%
   91684864/8147599360 ( 1.1%) @2.4x, remaining 52:43 RBU 100.0% UBU  85.7%
  102727680/8147599360 ( 1.3%) @2.4x, remaining 50:54 RBU 100.0% UBU  66.7%
  113803264/8147599360 ( 1.4%) @2.4x, remaining 50:35 RBU 100.0% UBU  85.7%
  124813312/8147599360 ( 1.5%) @2.4x, remaining 49:16 RBU 100.0% UBU  85.7%
  135823360/8147599360 ( 1.7%) @2.4x, remaining 48:10 RBU 100.0% UBU  85.7%
  146833408/8147599360 ( 1.8%) @2.4x, remaining 48:07 RBU 100.0% UBU  85.7%
  155385856/8147599360 ( 1.9%) @1.9x, remaining 48:00 RBU 100.0% UBU  85.7%
:-[ WRITE@LBA=12ce0h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:3978320 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m

---

### Post by Ghost Dog on 2009-06-01
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
DVDR/RW DD1601 15AF (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

ATAPI DVD DUAL 8X4X12 ATC1 (/dev/sr1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]
Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: splitting layers at 1754176 blocks
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=290h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:3508329 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 



? Still having issues.  Do I need a driver to "Unlock" my dual layer burning capabilities?

---

### Post by sladro on 2009-06-08
I'm having the same problem now, although I have burned 2 dvd+r dl disks in the last 2 days.

---

### Post by Ghost Dog on 2009-07-08
Weird.

---

### Post by Ghost Dog on 2009-09-13
I'm still having issues Burning Double Layer DVD's and I'm not sure if it's my TDK DL discs or not.

Is there a way I can simulate the burn process? so I can see if I need to get different discs?

I am using K3B, when I open an ISO it doesn't give me the option to simulate, is there a way to get it to simulate??

---

### Post by bomanizer on 2009-10-02
[https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/439281](https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/439281)

..if it's of any use

---

