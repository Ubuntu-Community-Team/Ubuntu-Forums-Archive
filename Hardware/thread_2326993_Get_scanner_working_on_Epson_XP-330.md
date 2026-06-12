---
title: "Get scanner working on Epson XP-330"
date: 2016-06-06
forum: Hardware
---

### Post by uli9 on 2016-06-06
Ubuntu 14.04 64bit. There seem to be no scanner drivers on the EPSON website. I installed the 2 available deb packages: epson-inkjet-printer-escpr_1.6.5-1lsb3.2_amd64.deb and epson-printer-utility_1.0.0-1lsb3.2_amd64. The printer worked after I installed the printer driver. So then I installed the printer utility hoping there is a scanner driver included. But SimpleScan cannot find a scanner, still. Not sure what it installed, as there is no utility software, at least not GUI.
Has someone an idea how to get the scanner to work?

---

### Post by him610 on 2016-06-06
Found two drivers for xp-330 at this webpage...

[http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult]("http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult")

Maybe they will work for you.

---

### Post by uli9 on 2016-06-06
him610, Those are the ones I installed. Thanks, though!

---

### Post by uli9 on 2016-06-07
To add another issue:
The printer driver installed fine on 14.04. But on 16.04 I get "Error: Dependency is not satisfiable: lsb (>= 3.2)". This is with gdebi. Also I get:

epson-inkjet-printer-escpr: missing-dependency-on-libc needed by opt/epson-inkjet-printer-escpr/cups/lib/filter/epson-escpr and 2 others
E: epson-inkjet-printer-escpr: debian-changelog-file-missing
E: epson-inkjet-printer-escpr: no-copyright-file
W: epson-inkjet-printer-escpr: unknown-section alien
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/cups/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/cups/lib/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/cups/lib/filter/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/cups/lib/filter/epson-escpr
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/cups/lib/filter/epson-escpr-wrapper
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/doc/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/doc/AUTHORS
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/doc/COPYING
W: epson-inkjet-printer-escpr: extra-license-file opt/epson-inkjet-printer-escpr/doc/COPYING
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/doc/NEWS
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/doc/README
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/doc/README.ja
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/lib64/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/lib64/libescpr.so
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/lib64/libescpr.so.1
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/lib64/libescpr.so.1.0.0
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/ppds/
E: epson-inkjet-printer-escpr: dir-or-file-in-opt opt/epson-inkjet-printer-escpr/ppds/Epson/

etc.

This is a new problem besides getting scanner drivers.

If this EPSON printer is a problem child, maybe someone could suggest a similar (small all-in-1) printer that is better compatible with Linux. I didn't have issues with the HP I had.

(I also have issues with the wireless, which is just another thing...)

---

