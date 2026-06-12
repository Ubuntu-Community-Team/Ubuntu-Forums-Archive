---
title: "what is 03:02.0 Unassigned class [ffff]: RaLink RT2561/RT61 802.11g PCI [1814:0301]"
date: 2010-08-28
forum: Hardware
---

### Post by abd_bela on 2010-08-28
Hi,
I added a wirlesscard to my PC running ubuntu and debian,  I did it the same thing to another PC running same distros and kernel with same drivers   firmware-iw..,  firmware-ralink, ....

On the second PC the card  runs correctly,

on my PC it seems not detected ???? 
the problem is probably not the driver, since on other machine, with the same firmware-ralink, the card is working.

the lspci  gave  
03:02.0 class [ffff]: RaLink RT2561/RT61 802.11g PCI [1814:0301] 

after update-pciids it gave
03:02.0_** Unassigned**_ class [ffff]: RaLink RT2561/RT61 802.11g PCI [1814:0301] 
the hardinfo program gives the list of pci card without  my wl card???

On the other machine I got, something like 

03:02.0_** Ethernet Controller **_: RaLink RT2561/RT61 802.11g PCI [1814:0301] 

please how to enable it ??
thanks for help
best regards

---

### Post by Fafler on 2010-08-28
Try another PCI slot? It could also be BIOS related. Try running lspci -vv and report the results.

---

### Post by abd_bela on 2010-08-28
Thanks a lot,
That 's what I've done , and it is working !!!!!  
Ah, ya ya , three days in serching drives and other support,!!!  just a bad slot!!!

thanks

---

