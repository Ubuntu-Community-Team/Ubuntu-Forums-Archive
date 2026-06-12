---
title: "Canon Driver with ndiswrapper"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by measekite on 2007-09-22
Posters have sucessfully used ndiswrapper with network cards enabling one to install the windows cd that comes with your wireless network card.

Has anybody ever installed ndiswrapper and then used the windows Canon CD that came with your printer and gotten the same results?

---

### Post by spd106 on 2007-09-22
NDISwrapper is specific to network hardware, see [http://en.wikipedia.org/wiki/Network_Driver_Interface_Specification](http://en.wikipedia.org/wiki/Network_Driver_Interface_Specification)

I can't see this being particularly useful for printers, even most network printers use standard network protocols such as IPP or SNMP, rather than some Windows specific protocol.

Perhaps WINE would be a closer match, but I think CUPS or some other printing system is your most likely source for successful printing. See [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

---

