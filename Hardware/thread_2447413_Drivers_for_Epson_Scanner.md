---
title: "Drivers for Epson Scanner"
date: 2020-07-18
forum: Hardware
---

### Post by daniell59 on 2020-07-18
My scanner is now running under Ubuntu 16.04. It would not work with later generations of Ubuntu. I don't know if that is still the case with Ubuntu 20.04 64. I would really like to have everything on one computer.

Scanner: Epson Perfection V30

Thanks

---

### Post by rbmorse on 2020-07-18
You'll need the Epson Linux scanner driver package, available here at no charge:[URL="http://support.epson.net/linux/en/iscan.php?model=gt-f720&version=2.30.4"]

http://support.epson.net/linux/en/iscan.php?model=gt-f720&version=2.30.4[/URL]

**BEWARE!**  The most recent package update precedes the release of 20.04. This could be a recipe for dependency issues.  I admit I haven't tried this with 20.04 but I can say from experience that it works fine with 18.04.  

The package contains the proprietary driver required by the scanner to operate under Linux. It also contains the proprietary iScan application that also must be installed even if you use a different front-end like The GIMP, simple-scan, Xsane or VueScan.  

You will find it well worth the time to read the entire installation instructions document _from inside the tarball_ before trying to install the software.   I've had best success with the individual packages method, but it is absolutely necessary that the three packages are installed in the order specified. 

A copy of the driver and iScan installation/user manual is available here: 

[http://download.ebz.epson.net/man/linux/iscan_e.html#sec6-1](http://download.ebz.epson.net/man/linux/iscan_e.html#sec6-1)

---

