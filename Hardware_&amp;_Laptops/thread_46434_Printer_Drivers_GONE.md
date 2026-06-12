---
title: "Printer Drivers GONE?"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by asimon623 on 2005-07-04
I've been trying to share my deskjet 5650 with my xp computers wirelessly for quite some time now, and I've been trying lots of different things...I think I may have messed up though and now my printer doesn't work locally either. System > Admin > Printers > Add printer now shows a lot less drivers and my printer is now not avaiable. I checked synaptic and the driver I need is installed (hpijs) properly, but it doesn't show up. I also installed HPLIP...nothing. Not only am I missing the hpijs driver however, I seem to be missing a lot of printer brands...as the list used to be much longer. Any help would be great.

---

### Post by David Haas on 2005-07-05
You mean that if you list all the HP PPD files in the HP directory at /usr/share/cups/model/foomatic-ppds/HP, the file for your printer--HP-DeskJet_5650-hpijs.ppd.gz--is missing, as are others?
David Haas

---

### Post by Shiven on 2005-07-27
[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) <-- download your driver there... hope that helps you out :)

---

