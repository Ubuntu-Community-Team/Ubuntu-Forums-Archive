---
title: "Canon printer. No color please."
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by dalert0140 on 2006-08-31
I have a Canon S520 that's working excellent in Ubuntu after being automatically--gasp!!-- recognized. How can I make it print in black only?
In windows the drive had an option to print everything in "grayscale" and since I don't want to buy all the different and pricey color cartridges to print document texts, that's the option that I used the most. Any fellow Canon users --or anyone really-- know how to get this going in ubuntu?

---

### Post by mssever on 2006-08-31
My printer is an HP, so this might not work for you, but...

Go to System > Administration > Printers. Right-click on your printer and choose properties. Switch to the Advanced tab, and the options you're looking for are in the Printout Mode drop-down. Some programs, e.g. OpenOffice, can also set these settings temporarily from the print dialog.

---

### Post by dalert0140 on 2006-09-01
I only have two options Page Mode and Page Size. Do you think it might be because I'm using stock drivers?( the ones that Ubuntu installed, is there any other kind?)

---

### Post by mssever on 2006-09-01
Probably a driver issue, then. HP releases Linux drivers for their printers, so they're better supported--which is why I have an HP printer. I don't think that Canon produces Linux drivers. You might check [http://linuxprinting.org](http://linuxprinting.org).

---

### Post by dalert0140 on 2006-12-03
For other people who might be in the same situation:

1. Go to "http://localhost:631/admin" Here you can change the settings for your CUPS server.
2. Go to the "Printers" tab.
3. Click on the "Set Printer Options" button.
4. Change your settings. There are lots of things that can be changed that, at least for me, weren't available in the "Printing" menu of Ubuntu. You can change resolution, color quality and some other neat stuff.
5. When you get asked for your password use your regular administrator password. 

That's it.

---

