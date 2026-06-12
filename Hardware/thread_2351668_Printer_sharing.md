---
title: "Printer sharing"
date: 2017-02-05
forum: Hardware
---

### Post by Bob_Younkin on 2017-02-05
I have a network of 4 laptops that we use for tax preparation.  They share one printer.  I Just upgraded to 16.04 from 14.04 and I can't share the printer.  I can mark the printer "shared" but there is no "server" menu to publish the shared printer. Cups and samba are installed.

Bob

---

### Post by pdc on 2017-02-05
from the Printers gui box; 

top left on menu: server: ..... does that give you what you need?

is there anything in this that could help you or provide checks? [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Bob_Younkin on 2017-02-05
The problem was the gui box I had didn't have that server menu.

running sudo system-config-printer from a terminal did however give me the appropriate gui.

---

### Post by pdc on 2017-02-06
great; glad you could get it solved

---

