---
title: "Install Epson ET-2650 printer, remote via Samba"
date: 2017-03-29
forum: Hardware
---

### Post by John Nagle on 2017-03-29
I have a new Epson ET-2650 printer, which is connected to a Windows machine via USB. Works fine on Windows 7. I'm trying to print to this printer via a Samba connection. Unfortunately, the list of Epson printers doesn't include any of the ET-series printers. (These are the new "ink tank" machines; the printer costs more but the ink is much cheaper).

I've tried setting the make and model to "Generic PostScript Printer Foomatic/Postscript (recommended)".  Printing the test page results in printing the Postscript source as text, with the comment "If you can read this, you are using the wrong driver for your printer".

I tried looking on the installer CD-ROM for a PPD file, but didn't find one.

No PPD file for this printer here: [http://www.openprinting.org/driver/Postscript-Epson/](http://www.openprinting.org/driver/Postscript-Epson/)

Any ideas?


Ubuntu 14.04 LTS x64.

---

### Post by pdc on 2017-03-29
If I go to the Epson download site; for linux support [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and enter ET-2650, I get as in screenshot below

the generic driver they recommend seems to truly be generic for many of their printers [COLOR="#0000FF"]epson-inkjet-printer-escpr_1.6.13-1lsb3.2_amd64.deb[/COLOR] for 64bit machines;

hopefully that will work for you; let us know how it goes; interested to hear how the big ink tanks do as well; 

______________

are you all good with samba? This ubuntu wiki aims to cover this area if you want any refreshers [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

