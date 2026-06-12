---
title: "Cannon DR-3010C wont scan on UBUNTU 14.04"
date: 2014-08-22
forum: Hardware
---

### Post by Bernhardt_Garlipp on 2014-08-22
Hi Guys

I am trying to resolve the problem where our new DR-3010C scanner wont scan on UBUNTU 14.04 tried 12.04  couldn't get it working their either.
I followed this thread ([http://ubuntuforums.org/showthread.php?t=2065192&highlight=3010c](http://ubuntuforums.org/showthread.php?t=2065192&highlight=3010c)) as this problem was solved already, however it didn't help at all. Even before I tried doing these changes scanimage was detecting the scanner, however the error I received remained the same. I tried rebuilding the sane-backend. Code changes seem to be already in newst branch

Info

"scanimage -L" result 

device `canon_dr:libusb:003:006' is a CANON DR-3010C scanner

"scanimage -T" result

scanimage: sane_start: Error during device I/O

xsane also detects scanner perfectly but returns the following error

Failed to start scanner: Invalid argument

Any help would be appreciated.

---

### Post by pdc on 2014-08-22
Hi Bernhardt; welcome to the forums;

You call your device > Cannon DR-3010C

Do you mean the DR-3010C made by Canon? 

as you say, from last year this thread [http://ubuntuforums.org/showthread.php?t=2065192&highlight=3010c](http://ubuntuforums.org/showthread.php?t=2065192&highlight=3010c) shows successful resolution

.....and the SANE project ............. [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) .............reports **[COLOR="#008000"]good[/COLOR]** function 

can I suggest you contact the maintainers of the sane-canon_dr - SANE backend; who are listed on this page [http://www.sane-project.org/man/sane-canon_dr.5.html](http://www.sane-project.org/man/sane-canon_dr.5.html) and talk directly to them: they are the best to help you:

_______________

please come back to us when you have got things working and let us know what you did with their guidance; it all seems rather a challenge; your syntax in typing in code would need to be exact;

---

