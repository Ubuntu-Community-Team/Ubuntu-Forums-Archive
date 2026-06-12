---
title: "trusty: hp 7612 no printing or scanning"
date: 2016-11-11
forum: Hardware
---

### Post by brilyant on 2016-11-11
The printer is visible over the network.

At the beginning of the day I could print but not scan.

Attempts to make the scanning work have resulted in the loss of printing too.


System settings -> printers->properties yields:

Device URI    hp:/net/Officejet_7610_series?zc=HPD0BF9CDC55ED

Make and Model    HP Officejet 7610 Series, hpcups 3.14.3

Printer state    Stopped - Backend /usr/lib/cups/backend/hpaio does not exist!


I cannot discover how to install hpaio.  Can anyone help?

---

### Post by brilyant on 2016-11-11
Doh!  I've just realised I needed a tick alongside "enabled" in the printer menu.

---

