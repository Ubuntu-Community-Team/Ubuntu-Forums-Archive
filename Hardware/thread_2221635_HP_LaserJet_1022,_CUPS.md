---
title: "HP LaserJet 1022, CUPS"
date: 2014-05-03
forum: Hardware
---

### Post by mamboze on 2014-05-03
I have had problems with CUPS since 10.04, I'm now running 12.04 on a laptop, Samsung RV511 with an HP LaserJet 1022. The HP 1022 prints but only one or two pages before a page is half fed thru and this stalls the printing. 
Altho this sounds rather like a printer feed fault, it has only been apparent since I installed 12.04 about 6 weeks ago. Prior to that CUPs would, intermittently, load up jobs and just sit there "processing". This could be solved by turning the printer off and then on. While this fault (whatever its cause) no longer happens, I'm now faced with this new problem. This is a real hassle. Any help would be appreciated.

---

### Post by tgalati4 on 2014-05-03
My experience is that HP printers have a lot of hardware problems that look like software problems.  The fact that you have to reboot the printer is a clue.  Sometimes the processors in the printer go bad (delaminate or just crap out completely).  There are extensive logs in /var/log/cups.  Go through those and see if there are any clues.

Is this HP1022 on a network or USB connection?  If one, try the other.  Half-fed pages could be a network issue or the printer processor heats up then stops mid-page.  Turning it off allows the processor to cool so it can resume printing a few more pages.  Sometimes there are bad capacitors in the printers that cause them to act strange.

Look through the log files and post anything helpful.

Monitor the print process through the webpage [http://localhost:631](http://localhost:631) or using the *hp-toolbox*.

Software errors tend to be consistent.  Hardware errors tend to give different status messages depending on the fault.

Try deleting the printer and reinstalling it using *hplip*.  

The fact that you have had printing problems with both 10.04 and 12.04 is consistent with an intermittent hardware problem.  Does this laptop dual-boot into Windows?  If so, is the printing consistent in Windows?

---

