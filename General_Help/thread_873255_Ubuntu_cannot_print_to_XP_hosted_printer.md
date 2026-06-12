---
title: "Ubuntu cannot print to XP hosted printer"
date: 2008-07-28
forum: General Help
---

### Post by hhibob on 2008-07-28
I have a new installation of Ubuntu and need help accessing a printer on an XP machine running on the same network.
I set up the printer using Windows printer via Samba, which located my XP machine and the printer attached to it. I used the best driver recommendation I could find, since the exact drivers aren't available (Canon MP470 - using MP610 drivers). Everything appeared to install fine, however when I test my printer, nothing happens.
The XP machine is running Windows firewall, however I assume this is not an issue, since Samba located the XP machine and connected printer quite easily.
Thanks for your help.

---

### Post by ryanhaigh on 2008-07-28
The problem is more likely to be a driver incompatibility. If you want to/can test this attach the printer directly to your ubuntu machine and see if it works there.

This page indicates that you may have better luck using the MP160 driver:
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP470](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP470)

Or if you are not printing images you can use turboprint for free changing the quality to medium (or it may be low) so that the banner is not displayed on the printout. The output quality is more than satisfactory for standard printing just not photos.

---

### Post by hhibob on 2008-08-02
Thanks....you advice worked.

---

