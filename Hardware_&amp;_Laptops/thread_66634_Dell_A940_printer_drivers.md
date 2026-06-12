---
title: "Dell A940 printer drivers?"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by Alhazred on 2005-09-17
Chaps,
I just got started with Ubuntu (and linux in general) and things are going ticketty-boo.
Perhaps predictably, though, I can't find drivers for my Dell A940 printer/copier/scanner. Is this a lost cause?
Alhazred

---

### Post by David Haas on 2005-09-19
Alhazred--I believe that the Dell printers are manufactured by Lexmark. Lexmark probably makes their multifunction printers also. Lexmark does not supply drivers to the Linux community, as does HP. I see only two PPD files (drivers) listed for Dell printers in Ubuntu. They are in the Dell directory at /usr/share/cups/model/foomatic-ppds/Dell. They are Dell-M5200-Postscript.ppd.gz  Dell-S2500-Postscript.ppd.gz. They are not what you want, unfortunately.

This site is the standard one for information on Linux printing and printers: [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi).

And Turboprint sells well-made drivers for Linux. [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html).

David

---

### Post by Alhazred on 2006-10-30
Dave,

Thanks for the reply. After a bit of digging, this page seems to fit the bill:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5150](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5150)
Well, it looks like this will be a learning experience for me.

Mick

---

### Post by petermaina on 2007-10-14
Alhazred,
Were you able to get the Dell A940 drivers? I can't get my printer to work.

Peter

---

### Post by ant1060 on 2008-07-12
Hi! I have finally managed to get my Dell A940 all-in-one working in Hardy! Follow the instructions here : it's easy!
[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)
The Dell A940 is the same as the Lexmark X5150, apparently.

---

