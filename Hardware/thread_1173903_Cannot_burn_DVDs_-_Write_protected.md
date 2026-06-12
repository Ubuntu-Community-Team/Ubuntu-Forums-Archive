---
title: "Cannot burn DVDs - Write protected?"
date: 2009-05-30
forum: Hardware
---

### Post by coblenis on 2009-05-30
Hello,

I cannot burn DVDs in Ubuntu 9.04.  I have tried Brasero, GnomeBaker, the built-in CD/DVD Creator, and K3b.  I think the problem is "failed with SK=5h/WRITE PROTECTED" 

I have frigged with the permissions.  I can read and write, the cdrom group has read and write permissions.  What do I have to do so I can use my burner? 

> System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
Slimtype DVD A  DS8A1P CH71 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: splitting layers at 1412000 blocks
:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=5h/WRITE PROTECTED]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2824000 -dvd-compat -speed=2.4 -use-the-force-luke=bufsize:32m 



I have an HP DV6608ca laptop with a Super Multi 8X DVD±R/RW with Double Layer Support disc drive (DVD A DS8A1P).

---

