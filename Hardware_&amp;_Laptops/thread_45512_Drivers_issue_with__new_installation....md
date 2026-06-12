---
title: "Drivers issue with  new installation..."
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Martjc on 2005-06-30
Am a complete novice to Linux.  Like the look of Ubuntu.  Have only tried the 'live' disk as yet, will soon add a new HDD and install to that.  Only problem I find is that my AC97 Sound chip seems not to be supported.  Also true for my Lexmark x85 3in1 printer.  Have another printer on network - Xerox m760.  Anyone know if that would be supported?

---

### Post by jasmuz on 2005-06-30
[QUOTE=Martjc]Am a complete novice to Linux.  Like the look of Ubuntu.  Have only tried the 'live' disk as yet, will soon add a new HDD and install to that.  Only problem I find is that my AC97 Sound chip seems not to be supported.  Also true for my Lexmark x85 3in1 printer.  Have another printer on network - Xerox m760.  Anyone know if that would be supported?[/QUOTE]
 Hello there...
AC 97 sound chipset is supported via the i810_intel module.

Im running the same and it works.

---

### Post by David Haas on 2005-06-30
Hi Martjc--The Xerox m760 is probably well-supported by Ubuntu Hoary, since the distro contains the driver (PPD file) for it. It's located in the Xerox directory at /usr/share/cups/model/foomatic-ppds/Xerox. The file name is Xerox-DocuPrint_M760-sharp.upp.ppd.gz
. After selecting this printer in the Gnome printer manager GUI, you then select this driver by clicking through the directory tree to Xerox.

I hope this helps.

David

---

