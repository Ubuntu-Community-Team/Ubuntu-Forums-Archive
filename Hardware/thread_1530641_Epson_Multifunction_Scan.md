---
title: "Epson Multifunction Scan"
date: 2010-07-13
forum: Hardware
---

### Post by Rubidot on 2010-07-13
I have an Epson NX415, and I'm running Ubuntu 10.04 64bit.  I plugged in the printer, Ubuntu detected it and found the printing driver no problem - but it's also a scanner.  It's plugged in, but when I open Simple Scan, it says "No Scanners Detected."

How do I get the scanner working?

I've seen this thread: [http://guide.ubuntuforums.org/showthread.php?t=1266259&highlight=nx410](http://guide.ubuntuforums.org/showthread.php?t=1266259&highlight=nx410)

but I'm hoping there's a simpler way.

---

### Post by pdc on 2010-07-14
you either follow those instructions and download from the Epson site;

or go the SANE site: 

scanners for linux

[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

and install the sane-epson driver and that should get it going for you 

I use x-sane to scan (on a Canon) and it goes well

(X-sane is the front-end programme to drive the scanner)

---

### Post by IcarusR on 2010-07-14
> and install the sane-epson driver

There are no drivers in sane for this scanner, contrary to what pdc says.

Like the link you posted says you can download iscan from avasys site at the bottom of this page....

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

Once downloaded just double click on the .deb file & a Gdebi window should open allowing install. Then you should be able to scan with xsane.

---

