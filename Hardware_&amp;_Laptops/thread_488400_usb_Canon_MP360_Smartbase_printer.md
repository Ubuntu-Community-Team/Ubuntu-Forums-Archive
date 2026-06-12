---
title: "usb Canon MP360 Smartbase printer"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by _sluimers_ on 2007-06-30
Ubuntu won't find my printer.

gnome-cups-add can't find it. The printer port combobox is empty.
lsusb can find my Canon printer though.
When I try adding a printer through the CUPS website and turboprint and print a testpage it says 
"Printer not connected, will retry in 30 seconds.."

The URI I choose is usb://Canon/MP360%20Series
Linuxprinting recommendded me to use bj8pa06n.upp and put that in usr/share/cups/model/ so I did.

What am I doing wrong here?

---

### Post by _sluimers_ on 2007-07-31
Anyone? Any thoughts? I still am clueless here.

---

### Post by _sluimers_ on 2007-09-18
Well I solved it. The problem was in the USB rights. So I chmodded them.

---

