---
title: "Lexmark e234n Driver"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by gerardo1967 on 2007-06-11
I've been trying to install drivers for this printer, everything seems ok, but when printing i get all the gibberish and not the actual printing. The driver I'm using is the one for e230. Do you know if there is any updated driver for this printer, or what the problem may be?

THANKS

---

### Post by hummingbird59 on 2007-06-11
Have you looked on this page: [http://www.openprinting.org/printer_list.cgi?make=Lexmark](http://www.openprinting.org/printer_list.cgi?make=Lexmark) ?  You might need to try different drivers until you find one that works or you may be unlucky. I've heard that it can be difficult to find drivers for Lexmark printers. But look here ([http://www.openprinting.org/printer_list.cgi?make=Lexmark](http://www.openprinting.org/printer_list.cgi?make=Lexmark)), do a google search for your printer and just try different drivers on the system - admin- printing- add printers until you find one that works.  Good luck!

---

### Post by gerardo1967 on 2007-06-11
I was able to put it to work with the drivers I got from Lexmark. It does need to be tweaked though. I'm able to configure the printer if I run "lexprint" from terminal, but not from Pinting Administration Window.  And I can print ok, however the qeue does not clean itself once printed, so you have to go and clear it manually to keep on printing. Any way around that. BTW I downloaded the drivers from Lexmark for  Debian GNU/Linux. The message I get in Printer Properties in Printers for STATUS is: Unable to lookup host 'file' - Unknown host

---

### Post by JimGardner on 2008-05-06
I got my E234 to work with Ubuntu 8.04 using the 'Generic PCL 4 Printer - CUPS+Gutenprint v5.0.2 Simplified' selection in the "Generic" printers category. I'm not sure if this would make a difference with the E234n. Also, this selection seems to be a color printer, so you have to set it to grayscale.
Good luck...

---

