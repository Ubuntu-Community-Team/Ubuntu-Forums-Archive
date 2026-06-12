---
title: "Wireless Card"
date: 2008-09-06
forum: Hardware
---

### Post by Kadoskracker on 2008-09-06
I have a HP dv9000 laptop went from vista to ubuntu ( Recent release ) and having problems with the wireless configurations need some help... seems that the computer doesnt recognize that there is a card installed. My other laptop works completely and is still an HP. im not sure how to check. what to check or how to get it working.

---

### Post by mudguts on 2008-09-06
first step in my opinion is to get the model stats and look for the card specs.  
start here.  [http://search.hp.com/query.html?lang=en&submit.x=0&submit.y=0&qt=dv9000&la=en&cc=us](http://search.hp.com/query.html?lang=en&submit.x=0&submit.y=0&qt=dv9000&la=en&cc=us)

from there get the chipset and start tracking down the driver.  i.m sure someone here will help.    i had a similar issue with my msi wind but got it going finally :)

---

### Post by Artemis3 on 2008-09-11
I have the same: HP Pavilion dv9000. After searching, it seems some come with an intel chipset, others with broadcom, and mine with atheros. Still trying to make it work, lspci shows: 

03:00.0 Ethernet controller: Atheros Communications Inc. AR242X 802.11abg Wireless PCI Express Adapter (rev 01)

Tried 2 windows vista drivers with ndiswrapper and still no luck, tho ndiswrapper -l shows: netathrx : driver installed
device (168C:001C) present (alternate driver: ath_pci)

ath_pci module is blacklisted (doesn't work anyway).

Ubuntu 8.04.1 amd64.


I found this good page but no luck: [http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

---

### Post by Artemis3 on 2008-09-12
Solved it, not using ndiswrapper but by compiling a newer madwifi.

That means following instructions [here](http://ubuntuforums.org/showpost.php?p=5539164&postcount=19) (but using the madwifi svn branch mentioned [here](http://madwifi.org/ticket/1192)); and finally editing /etc/modules to add ath_pci at the end so that it works when rebooted.

Do note that the led remains amber, make sure the switch is to the right...

---

