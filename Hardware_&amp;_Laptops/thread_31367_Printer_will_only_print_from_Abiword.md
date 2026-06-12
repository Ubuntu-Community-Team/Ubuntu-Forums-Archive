---
title: "Printer will only print from Abiword"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by Skote1 on 2005-05-02
First I will say I am new to Linux overall,  I've had Ubuntu installed for several weeks now.  As far as what I am working with is the Canon MP390 printer.  After MUCH trial and error I found the BJC-7004 driver will work with the printer, but only in Abiword (& the Test Page) so far.  I've tried OpenOffice, Adobe Acrobat, Firefox, & Epiphany so far but nothing else is wanting to print.  The print job will show up in the status box, but will disappear after a few seconds without the printer evening recognizing a print job being sent. HELP!  I realize I should be glad that I even have the MP390 even working in AbiWord, but I would prefer and need the capability of OpenOffice and a web browser.  Thanks for any suggestions!!

---

### Post by Xerampelinae on 2005-05-02
I wonder if the lpq command says anything about your printer?

---

### Post by Skote1 on 2005-05-02
Tried the lpq command and it is as follows:

root@scott:/home/skote # lpq
BJC-7004 is ready
no entries
root@scott:/home/skote # lpq
BJC-7004 is not ready
Rank    Owner   Job     File(s)                         Total Size
1st     skote   75      Untitled                        1053696 bytes
root@scott:/home/skote # lpq
BJC-7004 is not ready
Rank    Owner   Job     File(s)                         Total Size
1st     skote   76                                      78848 bytes

The fist entry is without any print jobs, the 2nd is with one in OpenOffice, the 3rd is with Abiword.  I paused the printer in order to get the snapshots of the 2 pending print jobs.

---

