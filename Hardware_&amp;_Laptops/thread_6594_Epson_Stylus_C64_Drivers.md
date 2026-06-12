---
title: "Epson Stylus C64 Drivers"
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by kliam6 on 2004-11-29
I'm looking for drivers for the Epson Stylus C64 that will work with ubuntu. Please help!

---

### Post by calvinpriest on 2004-11-30
Here's some general info:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C64](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C64)

These drivers should be installed by default.

However, sounds like the printer drivers have some problems.  It might be worth considering buying a different printer, imho.  linuxprinting.org is a good place to check before shopping.

Hopefully someone else will have some more specific advice for you...

---

### Post by adbak on 2004-11-30
I think you'll be fine if you enable the Universe repositories and download both of these packages:
```
cupsys-driver-gimpprint
cupsys-driver-gimpprint-data
```

That worked for me and my Stylus C82.

NOTE: Be sure to erase any preexisting printer configurations, if any, before adding a new printer.

---

