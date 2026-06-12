---
title: "Canon G2010 scans but does not print"
date: 2021-06-18
forum: Hardware
---

### Post by Acharn on 2021-06-18
Ubuntu 20.04 detects my printer, and shows it in the Settings>Printers as G2010. If the printer is turned on, it shows as Ready. If the power is off, it shows as Stopped. The Model shows Canon G2020 series Ver.6.10 If I click on "Clean Print Heads" the printer does that, but when I try to print a test page it apparently goes to a bit bucket somewhere. The troubleshooter from the help menu says there's no obvious solution. The log from the troubleshooter is 37.5 K which is too large to add as an enclosure. Strangely, the scanner works fine (it's an all-in-one printer/scanner). I have not found any solution on the internet -- yet.

---

### Post by Acharn on 2021-06-23
The problem exists in Ubuntu 20.10 as well.

---

### Post by Acharn on 2021-07-29
I hope this is the right place. I'm trying to set up a Canon G2010 ink-jet printer on Ubuntu 20.04 LTS. The GUI shows it connected as Canon G2010. It shows the driver as Canon G20**20** series Ver. 6.10, and says that it's connected to localhost. The printer does not print. Strangely, to my mind, the scanner (it's an all-in-one) works just fine, although I haven't installed any specific program for TWAIN. CUPS is installed and working. I am preparing to collect the data to submit a bug report, but thought I should ask first in case somebody else has solved the problem. I haven't found anything in the forum, which surprises me because the Canon G2010 is very popular in Thailand. Ubuntu has an excellent guide to troubleshooting printers, but it looks pretty long. Lots of log files to be created or copied to the bug report. One of the reasons I like Ubuntu so much. I hope somebody can save me the work of preparing the bug report. The guide to debugging is 12 pages long, although not every section is applicable to my situation.

---

### Post by Acharn on 2021-08-03
Found the answer over at AskUbuntu. ```
sudo apt install printer-driver-gutenprint
```

---

### Post by Acharn on 2021-08-03
Found the answer over at AskUbuntu. ```
sudo apt install printer-driver-gutenprint
```
Works like a charm. It should not have been so hard to find.

---

### Post by coffeecat on 2021-08-04
Threads merged and merged thread moved to Hardware sub-forum.

Please do not start multiple threads about the same problem.

---

