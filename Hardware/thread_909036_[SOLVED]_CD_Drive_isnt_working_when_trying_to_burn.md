---
title: "[SOLVED] CD Drive isnt working when trying to burn an ISO image onto DVD"
date: 2008-09-03
forum: Hardware
---

### Post by Xero121690 on 2008-09-03
I seem to have problems trying to burn a 2GB iso image file onto a dvd
i tried making a dvd iso image with K3b but i get this error

  ```
  System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
DVDRW IDE 16X A089 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 16.4x1352KBps.
:-? resuming track#1 from LBA#0
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/2389405696 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1166702 -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m
```



I must also say that i tried burning a music cd and it worked so i dont know whats wrong with the drive 

Well im hoping you guys help me..
Really appreciate it...

---

### Post by Xero121690 on 2008-09-03
I really need help on this.. :(
Is it even possible to write a 2GB iso onto a DVD?

Can some one give me a good AVI to DVD program because so far 2 of the programs that i have dont work. At least they dont work with my drive >.>

Is there a way i can activate my drive or something so it can start burning DVDs.

I mean the Music DVDs work but why not the DVDs??
its a cd/dvd drive @_@

---

### Post by VMC on 2008-09-03
Maybe try at a slower speed. I noticed your burning at 16x. I use Brasero but that shouldn't make any difference. I've burned 4gig to a DVD/RW without any problems. But that only burns at 4x.

---

### Post by Xero121690 on 2008-09-03
Ohhh Thanx Dude It WORKED!!!
Yeah i had to slow down the speed for the dvd to burn.
I still dont know why it couldn't burn at 16X..
But its cool as long as i can burn it..
Now i can watch Strange Wilderness on my dvd  Lolz :)

---

