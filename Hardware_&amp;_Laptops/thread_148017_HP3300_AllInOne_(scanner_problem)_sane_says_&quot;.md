---
title: "HP3300 AllInOne (scanner problem): sane says &quot;Document feeder out of documents&quot;!"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by tom75 on 2006-03-21
I've got strange error with my sane (hpaio).
When I try to scan with scanimage, I've got:

scanimage: sane_start: Document feeder out of documents

But this printer/scanner has no Automatic Feeder!
The scanner is recognized:
scanimage -L
device `hpaio:/usb/HP_LaserJet_3300_3310_3320?device=/dev/usb/lp0' is a hp HP_LaserJet_3300_3310_3320 multi-function peripheral

Ubuntu 5.10

---

### Post by lazylawyer on 2006-06-06
I get exactly the same problem in Dapper Drake, using my HP LaserJet 3300.  Did you find a solution?

---

### Post by jocsch on 2006-08-10
I face this problem now too. Any solution?

---

### Post by bmolay on 2006-09-23
I had the same problem, and I figured out a way to fix it that is working well.

I downloaded the source from hp.  The package is currently up to version 1.6.9 .  I then unpacked the archive and changed into scan/sane.

There, I modified one line of a file called pml.c.  My modified file at that spot looks like:
[FONT="Courier New"] 

else if(status & [SIZE="2"]PML_SCANNER_STATUS_FEEDER_EMPTY)
   {
      if(hpaio->currentBatchScan == SANE_FALSE &&                           hpaio->currentAdfMode == ADF_MODE_AUTO)
      {
         stat = SANE_STATUS_GOOD;
      }
      else
      {
         stat = SANE_STATUS_GOOD;
         /* stat = SANE_STATUS_NO_DOCS; */ /* caused problem */
      }
   }
[/SIZE][/FONT]

I then did cd ../..  to get back to the top of the source tree
and did 
    ./configure
    make
    make install

and I have been scanning color images at all sorts of resolutions
using xsane directly and via gimp with success.  Now and then I get messages about device busy, but after a short while I can scan again.

---

