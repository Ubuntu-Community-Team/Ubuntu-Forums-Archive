---
title: "Problem with printer"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by mindaugasg on 2005-09-24
In Linux my printer doesn't print black color. Instead of black color it print with blue. Where could be a problem. My printer is hp 845c

---

### Post by mindaugasg on 2005-09-26
So, has somebody any ideas?

---

### Post by David Haas on 2005-09-26
mindaugasg--Well, could your black cartridge, but not the tri-color cartridge be empty? How did you install the printer, and what driver (PPD file) did you select? The easiest and preferable way to install is with the GUI Gnome Printer Manager at System>Administration>Printing. After selecting your printer, one selects the driver, which Ubuntu 5.04 has in its distro. In fact, it has 5 drivers for the HP 845C. These are in the HP directory at /usr/share/cups/model/foomatic-ppds/HP and are as follows. 
HP-DeskJet_845C-cdj670.ppd.gz
HP-DeskJet_845C-cdj880.ppd.gz
HP-DeskJet_845C-cdj970.ppd.gz
HP-DeskJet_845C-hpijs.ppd.gz
HP-DeskJet_845C-pcl3.ppd.gz
Sometimes, one works better than the others, so if you have black ink try the others. Give us a follow up.
David

---

