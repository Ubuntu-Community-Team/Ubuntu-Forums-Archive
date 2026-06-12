---
title: "SELPHY CP400 Printer not in list to Add"
date: 2013-11-14
forum: Hardware
---

### Post by hallmerle on 2013-11-14
I've searched high and low for any hint on how to add my CP400 printer in 13.04.  When I hit the Add button under printers, the only thing that shows up is my HP Laserjet and the Forward button is greyed out.  Same thing if I use CUPS localhost:631 in my browser.  lsusb indicates the CP400 is connected.  I've installed gimp-gutenprint which allows me to set up the printer in GIMP, but the only devices I can choose to print to are Default and the HP Laserjet, neither of which would most likely work.  So, seems like until I can Add the printer, it wouldn't work from there either.

Suggestions?

---

### Post by aikishugyo on 2013-11-15
I suggest to search the gimp-print mailing list for information on the SELPHY series and other dye-sub printers. These require an intelligent backend to manage the queue, as they are not true USB devices.
Support for the intelligent backend is in the CVS version of gutenprint, so if you want to download and compile it, you will get support. If you use 5.2.9, I think you should see some of the devices, but others have been blacklisted since they cannot work at all without the backend (some do, at least for single prints).

---

