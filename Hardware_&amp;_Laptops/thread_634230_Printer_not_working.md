---
title: "Printer not working"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by ChasGaskin on 2007-12-07
I have just installed Gutsy and it seems to be working OK but I cannot get my Kyocera FS 1600+ to print a test page. It seems to be installed but when asked to print a test page it prints reams of garbage.  I also have a Lexmark z13 which passes a blank page through the printer when trying to print a test page.  It seems the print codes are not being recognised by the printers software.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by ewr2san on 2007-12-10
A really good resource for seeing if a printer is supported is:
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)
and
[http://openprinting.org/printer_list.cgi?make=Anyone](http://openprinting.org/printer_list.cgi?make=Anyone)


The Kyocerra is listed as working
[http://openprinting.org/show_printer.cgi?recnum=Kyocera-FS-1600plus](http://openprinting.org/show_printer.cgi?recnum=Kyocera-FS-1600plus)

The Z13 looks much more chalenging... Looks like you need to download a driver from IBM.
[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z13](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z13)


You can try adding the kyocerra printer Directly via CUPS which runs localy.
Open a browser to: [http://localhost:631/](http://localhost:631/)

---

