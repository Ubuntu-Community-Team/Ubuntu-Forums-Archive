---
title: "Linksys Print Server WPS-54G"
date: 2009-05-19
forum: Hardware
---

### Post by gnulab on 2009-05-19
Hi,

I just want to share my findings when installing a printer that is connected to a print server
brand: linksys
model: WPS54G

Printer attached:
brand: hp
model: LaserJet p2015d

The way to make ubuntu prints is via IPP, not LPR/LPD option (since that's what's used when it's under WinXP).

After reading several posts, the way to install printer is thru
System -> Administration -> Printing

If we click New -> Printer, we find that the system automatically tries to detect printer that is connected physically. However, in this case, the printer is connected wirelessly via a device, before ubuntu wouldn't be able to 'see' the printer, so definitely, it fails to find it.

Then we'll be presented with a window titled "Select Device". Choose Network Printer (see the mini triangle beside it? Click it and it will expand) and choose Internet Printing Protocol.

Host: <fill in the IP address of your WPS54G (you ought to have assigned a static IP beforehand)>
Queue: /printer/<you can fill whatever you want, but normally model of the printer> (at this part, it's not very intuitive for users with Win98 background, maybe the developer should have a tooltip) 

After the Queue part is filled, then the FORWARD button isn't greyed out anymore, and you'll be presented with Select Printer Driver (as per WinXP).
(The opposite of what happen in WinXP, we choose the driver first, then change the port option.)

After selecting the appropriate printer driver, you're good to go!

Hopefully this helps in people trying to install their printers that's connected via Linksys WPS54G, however I'm quite sure this is equally applicable to other simple print server devices, such as Edimax, Dlink, etc.

Henry

---

