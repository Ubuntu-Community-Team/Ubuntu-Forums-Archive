---
title: "Printing from Windows 7 to shared printer on Ubuntu 10.10 - Completed but no print!"
date: 2011-03-18
forum: Hardware
---

### Post by mindseye1 on 2011-03-18
I just finished installing Ubuntu 10.10 64-bit and I am trying to share the connected printer (Samsung ML-2510 Laser) with a Windows 7 machine on the network. I've enabled sharing on the printer and followed this guide to get everything running: [http://www.liberiangeek.net/2010/12/share-printer-ubuntu-10-0410-10-maverick-meerkat-windows-print/](http://www.liberiangeek.net/2010/12/share-printer-ubuntu-10-0410-10-maverick-meerkat-windows-print/)
In addition to the settings shown in the guide, I also set 'guest ok = yes'.
On the Win7 machine I can add the printer, install the driver (Samsung Universal Print Driver) and I can attempt to print a test page. I can hear the printer warm up, and the print queue on the Ubuntu machine shows my print job, but it says 'Completed'. No test page ever comes out of the printer.
Also, the printer does work fine from Ubuntu. So... any ideas?

Thanks for the help!
~mindseye1~

---

### Post by mindseye1 on 2011-03-21
Just a little bump to see if anyone else has ideas.

---

### Post by stults on 2011-04-26
Sorry I could not get to you earlier.  I would highly recommend using the PCL5 drivers for your Windows 7 machine to install the printer with.  Universal drivers can sometimes have issues with certain printer and PCL6 can have some issues with certain printers or applications.  I have seen this occasionally come up with both HP and Samsung drivers (universal and PCL6).  PCL5 is older, simpler and generally much more widely compatible with printers and applications.  Good luck!

---

