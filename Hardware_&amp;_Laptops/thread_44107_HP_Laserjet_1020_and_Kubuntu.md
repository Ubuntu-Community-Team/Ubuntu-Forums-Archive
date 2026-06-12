---
title: "HP Laserjet 1020 and Kubuntu"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by Pointwood on 2005-06-24
I have just bought such a printer, but I can't seem to get it to work :(

I first tried to add it with the KDE Add Printer Wizard, but the printer wasn't there. there was a 1022 model, so I tried that, but that didn't work.

Then I found this page: [http://support.ideainformatica.com/hplj1020/](http://support.ideainformatica.com/hplj1020/)

but "make install-hotplug" fails. It complains about a missing /etc/hotplug/usb.usermap. There is a usb.handmap however, so stupid me tried making a copy of than and named it usb.usermap. That made it install at least...

If I run "usb_printerid /dev/usb/lp0" I get: "Error: Permission denied: can't open '/dev/usb/lp0'"

At some point I did get something that looked correct, just like it shows on that page, but I managed to bork that somehow :(

Also the Add Printer Wizard doesn't work anymore - at the "Printer Model Selection" page, it should show all the printer models it knows, but it shows nothing now :(

Anybody got some hints?

---

### Post by David Haas on 2005-06-25
Pointwood--You've got a tough problem, but perhaps some of the experts in the Forum can help you. You may already know about these two important sites for printing under Linux: (1) [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi), (2) [http://h10018.www1.hp.com/wwsolutions/linux/products/printing_imaging/index.html](http://h10018.www1.hp.com/wwsolutions/linux/products/printing_imaging/index.html). Neither shows the HP Laserjet 1020 as supported. And I see no PPD file for the 1020 at /usr/share/cups/model/foomatic-ppds/HP.
David

---

### Post by Pointwood on 2005-06-26
Yeah, you're right :( However it does look like someone did get it to work as you can see in that link above.

I've written a mail to HP, requesting info about why it isn't supported.

---

