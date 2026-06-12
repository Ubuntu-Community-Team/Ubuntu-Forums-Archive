---
title: "K3b can't burn DVDs anymore"
date: 2008-08-05
forum: General Help
---

### Post by self-defence on 2008-08-05
Hi,

I don't know I haven't changed anything major in the last few weeks but I tried to burn a DVD (tried again and again with restart and reinstall of K3b) but I always get the same error.

Anyone have any ideas what could be wrong with this?
I tried burning a CD with no problems just DVDs.

Thanks for the help and please help. :(

Bye

K3b Debug output:
```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HL-DT-ST DVDRW  GSA-S10N AP09 (/dev/scd0, /dev/sg0) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 1825942 (3739529216 bytes)
Pipe throughput: 34723840 bytes read, 34719488 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
    1114112/3739529216 ( 0.0%) @0.0x, remaining 335:33 RBU 100.0% UBU   2.9%
    1114112/3739529216 ( 0.0%) @0.0x, remaining 559:15 RBU 100.0% UBU 100.0%
    1114112/3739529216 ( 0.0%) @0.0x, remaining 727:01 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=220h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1825942 -speed=4 -overburn -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
1825942
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using STAR_TREK_VIII_FIRST_CON000.AVI;1 for  Star Trek VIII First Contact/Star Trek VIII First Contact cd2.avi (Star Trek VIII First Contact cd1.avi)
  0.03% done, estimate finish Tue Aug  5 11:26:36 2008
  0.06% done, estimate finish Tue Aug  5 11:26:36 2008
  0.08% done, estimate finish Tue Aug  5 11:26:36 2008
  0.11% done, estimate finish Tue Aug  5 11:26:36 2008
  0.14% done, estimate finish Tue Aug  5 11:26:36 2008
  0.17% done, estimate finish Tue Aug  5 11:26:36 2008
  0.19% done, estimate finish Tue Aug  5 11:26:36 2008
  0.22% done, estimate finish Tue Aug  5 11:26:36 2008
  0.25% done, estimate finish Tue Aug  5 11:26:36 2008
  0.27% done, estimate finish Tue Aug  5 11:26:36 2008
  0.30% done, estimate finish Tue Aug  5 11:26:36 2008
  0.33% done, estimate finish Tue Aug  5 11:26:36 2008
  0.36% done, estimate finish Tue Aug  5 11:26:36 2008
  0.38% done, estimate finish Tue Aug  5 11:26:36 2008
  0.41% done, estimate finish Tue Aug  5 11:26:36 2008
  0.44% done, estimate finish Tue Aug  5 11:26:36 2008
  0.47% done, estimate finish Tue Aug  5 11:26:36 2008
  0.49% done, estimate finish Tue Aug  5 11:26:36 2008
  0.52% done, estimate finish Tue Aug  5 11:26:36 2008
  0.55% done, estimate finish Tue Aug  5 11:26:36 2008
  0.58% done, estimate finish Tue Aug  5 11:26:36 2008
  0.60% done, estimate finish Tue Aug  5 11:26:36 2008
  0.63% done, estimate finish Tue Aug  5 11:26:36 2008
  0.66% done, estimate finish Tue Aug  5 11:26:36 2008
  0.68% done, estimate finish Tue Aug  5 11:26:36 2008
  0.71% done, estimate finish Tue Aug  5 11:26:36 2008
  0.74% done, estimate finish Tue Aug  5 11:26:36 2008
  0.77% done, estimate finish Tue Aug  5 11:26:36 2008
  0.79% done, estimate finish Tue Aug  5 11:26:36 2008
  0.82% done, estimate finish Tue Aug  5 11:26:36 2008
  0.85% done, estimate finish Tue Aug  5 11:26:36 2008
  0.88% done, estimate finish Tue Aug  5 11:26:36 2008
  0.90% done, estimate finish Tue Aug  5 11:26:36 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Filmi -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-user/k3baU0ZMa.tmp -rational-rock -hide-list /tmp/kde-user/k3bhbW6Wb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-user/k3bTXidVb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-user/k3bE1awrc.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Filmi -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-user/k3boGsUMa.tmp -rational-rock -hide-list /tmp/kde-user/k3bi9Q0Ba.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-user/k3b4POEna.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-user/k3bhZ67qc.tmp 

```

---

### Post by self-defence on 2008-08-09
One other thing I have noticed is that if I try to burn a DVDRW it works with out any problems.

I'm a little baffled by all this it seems only DVDs can't be written. I'd like to try if sometimes it work or sometimes it doesn't but since it destroys the DVDs I seem to be running out.

Anyone have any ideas what the devil is going on with my recorder?

Do I need to provide any other info?

Thanks and bye.

---

### Post by stinger30au on 2008-08-09
do you have a spare dvd burner to drop in to the pc and test just to prove if the drive itself is ok or not?

---

### Post by rbmorse on 2008-08-09
If the drive burns "RW" disks I would think the software side is working.  Maybe you have a bad "R" blank disc, perhaps a bad batch. Have you tried different media?

---

### Post by self-defence on 2008-08-09
Unfortunately it is a laptop(Apple MacBookPro) so I'm not able to change the drive. I have already thought that the batch of DVDs might be at fault but they seem to work quite well in another PC(WinXP, Nero) witch I've been using to burn DVDs. 
I've just thought of a way that I might possibly be able to test my drive. Since I can't run an Ubuntu live CD and record at the same time I'll try in MacOS but that will still only tell me if the device is working but not if the fault is in the system or software.

Thanks for now and I'll report back as soon as I have tested it.

---

### Post by self-defence on 2008-10-21
Ok now I'm really stumped. I've just tried to burn another DVD.
And I was not successful but then I tried again and it worked. So I backed tracked what happened and figured out this. If I tried to burn a DVD with the Windows + Linux file system it worked but if I tried with Joliet mode it didn't work. I kept getting the same error.
For now I have no idea why with Joliet it didn't work and if someone might have an idea why it doesn't work.

Anyway thanks for the help.

Bye

---

