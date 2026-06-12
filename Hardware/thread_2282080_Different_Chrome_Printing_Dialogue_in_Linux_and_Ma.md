---
title: "Different Chrome Printing Dialogue in Linux and Mac"
date: 2015-06-11
forum: Hardware
---

### Post by ufarmer on 2015-06-11
I seem to be able to print properly to a Xerox 7755 WorkCenter except for .pdf files.  Apparently everyone has some problem with this associated with a failure of the machine to validate accounting information when printing .pdfs.  A workaround that seems to work for everyone using a Mac is to open the file in Chrome and then print using the options in the "Print using system dialogue" window.  When I try to do the same thing, I do not get the same dialogue window nor can I find the same options anywhere else.

Any advice is appreciated.

---

### Post by weatherman2 on 2015-06-11
The "print using system dialogue" option means use the OS's built-in printing mechanism to print.  And the options you get with that depend largely upon the printer driver - what options are written into it.  Unfortunately, many Linux printer drivers, in my experience, don't offer the same printer options that you might find on the Windows or Mac versions.  For a long time, I used Canon's own Linux drivers for my printer, but had severely limited print options (e.g. no B&W printing).  Finally, I switched to the latest Gutenprint which, for me, allowed me to print using a native driver (with a lot of options) and not Canon's limited driver.

So what can you do?  Try using a different printer driver.

Or - find another solution for printing PDF files instead of the Chrome work-around.

---

### Post by ufarmer on 2015-06-11
Thanks.  My understanding is that Macs run on top of Linux.  So I just find it odd that there are discrepancies with the drivers.  The option in the Mac dialogue that seems to be the difference is something like "use Xerox settings" -- which seemed like a Xerox thing rather than a Mac thing.

It looks like I already have Gutenprint installed in Ubuntu 14.04.  How can I get CUPS to use that instead of the Xerox .ppd I have it pointing to now?

---

### Post by weatherman2 on 2015-06-11
Actually, Macs do not "run on top of Linux."  Mac OS is based on NeXSTEP and BSD - which is sort of a cousin to Linux, but the drivers are usually completely different.  It's typical for a hardware manufacturer to write good Mac drivers but no Linux drivers at all - or substandard Linux drivers.

You have to use whatever printer drivers you can find.  Some drivers may be included with Ubuntu that will support your printer.  Sometimes the manufacturer writes different drivers and makes them available on the manufacturer's website for Ubuntu.  It's not simply a matter of replacing a PPD file.

---

### Post by ufarmer on 2015-06-12
Perhaps I misunderstand.  I thought Gutenprint was a suite of drivers.  If so, I was not asking about replacing the .ppd file but rather getting CUPS to stop using the current .ppd file and switch to some driver in the Gutenprint suite.  Gutenprint appears to support an earlier Xerox WorkCentre.  There's a .ppd file for this printer too, but I was asking about how *not* to use the .ppd file.

---

