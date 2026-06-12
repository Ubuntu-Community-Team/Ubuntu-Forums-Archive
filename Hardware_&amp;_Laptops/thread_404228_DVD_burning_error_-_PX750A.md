---
title: "DVD burning error - PX750A"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by Rastan836 on 2007-04-08
Wasn't sure best place to post this...

Having trouble burning DVD's. I have a Plextor (PX-750A) drive and am using Verbatim 8x DVD-R's. I can boot into XP and burn with no problems, but to hafta do that anytime I want to burn a disc is not something I wanna hafta do, obviously.

I tried some test burns with a Verbatim DVD+RW several times and have no better luck there either.

Even trying to burn as root doesn't help.

Here is the error report from k3b:

```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
ASUS CRW-4832AS 0.67 (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

PLEXTOR DVDR   PX-750A 1.03 (/dev/scd0, /dev/sg4) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; SAO/R96P; SAO/R96R; Restricted Overwrite; Layer Jump]
Used versions
-----------------------
growisofs: 6.1
mkisofs: 2.1.1a03-unofficial-iconv

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.02% done, estimate finish Sun Apr  8 04:32:26 2007
  0.05% done, estimate finish Sun Apr  8 04:32:26 2007
  0.07% done, estimate finish Sun Apr  8 04:32:26 2007
  0.10% done, estimate finish Sun Apr  8 04:32:26 2007
  0.12% done, estimate finish Sun Apr  8 04:32:26 2007
  0.15% done, estimate finish Sun Apr  8 04:32:26 2007
  0.17% done, estimate finish Sun Apr  8 04:32:26 2007
  0.20% done, estimate finish Sun Apr  8 04:32:26 2007
  0.22% done, estimate finish Sun Apr  8 04:32:26 2007
  0.25% done, estimate finish Sun Apr  8 04:32:26 2007
  0.27% done, estimate finish Sun Apr  8 04:32:26 2007
  0.30% done, estimate finish Sun Apr  8 04:32:26 2007
  0.32% done, estimate finish Sun Apr  8 04:32:26 2007
  0.35% done, estimate finish Sun Apr  8 04:32:26 2007
  0.37% done, estimate finish Sun Apr  8 04:32:26 2007
  0.40% done, estimate finish Sun Apr  8 04:32:26 2007
  0.42% done, estimate finish Sun Apr  8 04:32:26 2007
  0.45% done, estimate finish Sun Apr  8 04:32:26 2007
  0.47% done, estimate finish Sun Apr  8 04:32:26 2007
  0.50% done, estimate finish Sun Apr  8 04:32:26 2007
  0.52% done, estimate finish Sun Apr  8 04:32:26 2007
  0.55% done, estimate finish Sun Apr  8 04:32:26 2007
  0.57% done, estimate finish Sun Apr  8 04:32:26 2007
  0.60% done, estimate finish Sun Apr  8 04:32:26 2007
  0.62% done, estimate finish Sun Apr  8 04:32:26 2007
  0.65% done, estimate finish Sun Apr  8 04:32:26 2007
  0.67% done, estimate finish Sun Apr  8 04:32:26 2007
  0.70% done, estimate finish Sun Apr  8 04:32:26 2007
  0.72% done, estimate finish Sun Apr  8 04:32:26 2007
  0.74% done, estimate finish Sun Apr  8 04:32:26 2007
  0.77% done, estimate finish Sun Apr  8 04:32:26 2007
  0.79% done, estimate finish Sun Apr  8 04:32:26 2007
/dev/scd0: "Current Write Speed" is 8.2x1385KBps.
:-[ WRITE@LBA=0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
```


Any help will be most appreciated.

---

### Post by Rastan836 on 2007-04-15
No ideas about this?

Anyone? :)

---

### Post by Rastan836 on 2007-05-07
Well, upgrading to Feisty seemed to fix the main problem. I am now able to burn a DVD... and must say am most impressed with Feisty so far, as the overall performance of my comp has taken a giant leap in the right direction :)

However, burning on a 8x DVD-R took about 90 mins! I used Nero this time, but am sure the result would have been the same with k3b. I ran simulations using both apps, which I cancelled due to the amount of time it was taking. Decided to go ahead and try a real burn, hoping it would be ok.

The burn was successful with no errors.. did verify as well as then copying data from the disk back to the HD to make certain.

A bit of searching suggested that I needed to enable DMA. 

```
hdparm -d1 /dev/scd0
```

resulted in this:

```
/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```


Any suggestions are welcome...

Thanks!

---

### Post by derekguy on 2007-05-17
I get that exact error also but when I was using Edgy I was able to set DMA to on and had no issues with it.

I am using a Compaq Presario B1800 laptop with a DVD Multi Recorder. It is a Mashita DVD-RAM UJ-84OS.

Any help appreciated,
Derek

---

