---
title: "HP printer prints 1/2 CUPS test page at beginning of every print job."
date: 2017-04-06
forum: Hardware
---

### Post by THUNDER233 on 2017-04-06
Linux: Ubuntu 16.04
Printer: HP Envy 5530
Hplip: 3.16.3

The first page of every print job is similar to the test page from 'System Settings'>'Printer'.
It has 'Unclassified' at the top. Colored circles are missing.
Bottom half of page has Specs for the printer and print job.
This problem was in 14.04 also.
Have read CUPS web pages and hplip web pages - no joy.
Anybody got any ideas on how to fix?

---

### Post by Autodave on 2017-04-06
Did you install any drivers? If so, what ones?  How is the printer connected to the PC?

---

### Post by THUNDER233 on 2017-04-06
USB Connection
 No drivers required

---

### Post by pdc on 2017-04-06
If you go to the PRINTERS folder; and right-click on the only? icon that is there for your printer; select properties; can you tell us what it says for Device URI and what is in MAKE & MODEL please?

---

### Post by THUNDER233 on 2017-04-06
HP Envy 5530 Series, hpcups 3.16.3

hp:/usb/ENVY_5530_series?serial=CN482261WX05XT

---

### Post by pdc on 2017-04-07
better see if there is an HP support network: how long have you had the printer ...........

---

### Post by THUNDER233 on 2017-04-07
Printer was shipped 11/27/2014.

---

### Post by ^83%u#@^ on 2017-04-07
Try delete printer and use hplip software  [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by THUNDER233 on 2017-04-07
Read first post.
Hplip: 3.16.3 is already installed.

---

### Post by THUNDER233 on 2017-04-07
Goto 'Files'
Ctrl h

scroll down to '.cups'
open '.cups'' file

should find one text file 'lpoptions'
open file
Mine reads: 'Default HP-ENVY-5530-series job-sheets=unclassified,none'
The first part I believe is correct (Default HP-ENVY-5530-series)
Anyone know what the rest means?

The information at :[https://www.cups.org/doc/options.html](https://www.cups.org/doc/options.html) does not seem to match what I have.

---

### Post by ^83%u#@^ on 2017-04-07
i think job-sheets=unclassified,none' means that you must clean printer-jobs

---

### Post by pdc on 2017-04-07
can you tell us again which file you have looked into please? the cups directory is usually in /etc

---

### Post by THUNDER233 on 2017-04-08
Should be : Files>Home >Ctrl H
Scroll down to : .cups

---

### Post by THUNDER233 on 2017-04-09
job-sheets prints the first and last pages as banner sheets. You have
it set for no last page and a first pages headed "unclassified". Is this
what you want? "job-sheets=none,none" would be more usual.

Solves the problem.

Two days ago I deleted 'lpoptions' file to see what would happen.(saved to flash drive)
The page I printed was the size of a postage stamp in the left hand corner of a sheet of paper.
I knew I was on the right track.

Changing part of text to "job-sheets-none,none" solved the problem.

---

