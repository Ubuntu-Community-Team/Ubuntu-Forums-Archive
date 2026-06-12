---
title: "Ubuntu 12.04 cannot print to HP Color LaserJet 5550"
date: 2013-02-04
forum: Hardware
---

### Post by 7seastraveller on 2013-02-04
Upgraded from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS a week ago, cannot print to HP color LasorJet 5550 since then. Was printing fine with Ubuntu 10.04!
 
With Ubuntu 12.04, I can only print test page, but cannot print anything other than that. All printing jobs were sent to the printer, then "Stopped". cannot resume.
 
Tried everything I could find from the internet and forums.
 
Uninstaledl all drivers, I even uninstalled printer gnome. Then re-install. tried Ubuntu 12.04 software center, HP Linux Imaging and Printing directly. Nothing works.
 
Tried tricks like chmod cups backend, hp-check, everything was fine. Printer Status "Ready to Print", Nothing in error log. Just CANNOT PRINT.
 
Please HELP!

---

### Post by 7seastraveller on 2013-02-04
Use URI via the CUPS interface (use a browser):
[http://localhost:631/jobs/](http://localhost:631/jobs/)
 
State shows "stopped" with "/usr/lib/cups/filter/pdftops failed"
 
checked "/usr/lib/cups/filter/pdftops failed", it appears to be a cups 1.5.3 bug.
 
[https://bugs.mageia.org/show_bug.cgi?id=6819](https://bugs.mageia.org/show_bug.cgi?id=6819)
 
Trying to see if there is any workaround. :(

---

### Post by 7seastraveller on 2013-02-04
Digged more:
 
There are plenty bug reports regard the new CUPS cannot print on network printer anymore, but no fix yet.
 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/973270](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/973270)
[bug 992982]("https://bugs.launchpad.net/bugs/992982")
[bug 992468]("https://bugs.launchpad.net/bugs/992468")
[bug 990734]("https://bugs.launchpad.net/bugs/990734")
 
The fix is supposed to be in:
cups 1.5.3-0ubuntu2
and release of 12.04.1.
 
Question: 12.04 LTS is supposed to be a stable release, why waste everybody's time and release a version with such a wide spread severe level problem??? :???:

---

### Post by 7seastraveller on 2013-02-05
Before found out "/usr/lib/cups/filter/pdftops failed" is a CUPS 1.5.3 bug, I tried everything I could including standing on one hand. :wink: Trying to find out what is wrong because the printer was working fine with Ubuntu 10.04 for years. 
 
So if you have the same problem as me, don't waste your time as none of the following works:
 
Tried uninstalling all printer drivers, not just HP, I mean ALL.
Uninstalling CUPS altogether.
Uninstalling printer-gnome.
Uninstalling a big chunk of Desktop.
Clean up after uninstallation.
 
I did so because I suspected it may caused by a faulty in OS upgrade from 10.04 to 12.04 and left too much junk behind.
 
After everything was wiped clean, I installed directly from HP Linux Imaging and Printing website. 
Then held my breath for 5 minutes. (world record of static apnea is 11 minutes, so I'm fine, didn't pass out!)
 
You already know the result, NOTHING WORKS. Just cannot print to my fancy color laser printer.
 
Don't even think about downgrade your CUPS to 1.5.2-9, there is a juicy bug over there to stop you downgrade.
"CUPS downgrading to 1.5.2-9 failed - cannot revert back to 1.5.3 now"
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1033000](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1033000)
 
Before I cry over my color laser printer, there is a Workaround, print to PDF file first, then open the file from Adobe and print, that works.

---

### Post by 7seastraveller on 2013-02-05
BUG Reported to Launchpad: #1116513
 
The newest CUPS update lets /usr/lib/cups/filter/pdftops call "pdftops -origpagesizes"
to fix a bug and apparently this generates a new bug here:
 
(pdftops) crashed on signal 8!
(/usr/lib/cups/filter/pdftops) stopped with status 8
 
It appears that the problem is caused by SIGFPE Floating Point exception (signal 8). and the root cause is in poppler-tools that an uninitialized variable leading to a division by zero!

---

