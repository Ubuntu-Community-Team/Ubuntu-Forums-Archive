---
title: "Removing Printer Drivers?? - Edgy"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by Erlander on 2007-03-09
I have been trying to install printer drivers for 2 Canon printers and have not been successful in getting them to print.

If I go to System/Administration/Printing and right click on a printer and then select remove the printer icon goes.  However if I then attempt to re-install the driver I get a message telling me that the driver is already installed.

So I can start from fresh how do I remove those drivers?

My most recent driver install attempt was from this guide:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

Thanks in anticipation.

Rob

---

### Post by teaker1s on 2007-03-09
alien changes rpm to deb package for example, so
```
gksudo synaptic
```
search the package names and uninstall them

---

### Post by Erlander on 2007-03-10
Tweaker1s,

Thank you.

When I tried to uninstall the packages in Synaptic it told me to fix the broken packages first.

So i reinstalled all of them and then worked through the guide.

Success this time.

Thank you.

Rob

---

