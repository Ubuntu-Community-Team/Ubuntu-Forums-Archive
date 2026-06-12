---
title: "HP 720c printer - painfully slow"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by boystrus on 2005-06-16
My HP 720c printer - although working - is painfully slow in printing documents - even if set at economy, 8bt ..

it is also erratic, ranging between deadeningly slow to crindingly slow...

does anyone know the problem?

i am using the standard Ubuntu driver for the device - is this a common problem?

---

### Post by David Haas on 2005-06-16
Hi boystrus--When printers are set up correctly, they should work as quickly in Ubuntu as in Windows. My HP Deskjet 5740 prints perfectly. In general, HP printers work as well or better than other brands in Linux. 

Did you install the printer using the Gnome print manager (System>Administration>Printing)? If so, were you able to select your model from the list? Did you then select the driver (PPD file) for your printer? I see it listed as HP-DeskJet_720C-pnm2ppa.ppd.gz in the following directory: /usr/share/cups/model/foomatic-ppds/HP. When the PPD file has been selected, Linux places an unzipped copy of it in /etc/cups/ppd. Look for it here.

Also, you need to be sure that you have the cupsys and foomatic packages installed. They should be by default, but you can check this in Synaptic package manager in System>Administration>Synaptic Package Manager.

Well, check it out and let us know how it goes.

David

---

