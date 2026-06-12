---
title: "&quot;/usr/lib/cups/backend/cnij_usb failed&quot; - Canon iP4200"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by mhueting on 2006-10-18
My canon iP4200 won't print.

When I look at CUPS (localhost:631) I see this in the printers tab:

"/usr/lib/cups/backend/cnij_usb failed"

And if I press "Start printer"  nothing happens. I can also see a little icon on the right in the task bar of a printer with an exclamation mark next to it. At all the jobs it says "printer stopped".

What to do? I'm kind of lost here :confused:

---

### Post by mijj on 2007-05-04
same here

<waits patiently in queue for expert>

---

### Post by darthsappho on 2007-05-12
When I added the printer, it gave me two options - "Canon iP4200 USB #1" and "USB Printer #1 with status readback from Canon IJ". I randomly picked the second option, and got the "/usr/lib/cups/backend/cnij_usb failed" error. When I added the same printer again and chose the first option, it worked. The Connection tab on the printer properties dialogue will tell you what you've got; if it's USB Printer #1, it will show both options under Detected Printers (but won't save changes), if it's Canon iP4200 you'll see Network Printer usb://Canon/iP4200.

Also, the default paper source is Paper Feed Switch, which doesn't work - change that to Auto Feeder.

Hope that helps.

---

### Post by darthsappho on 2007-05-12
Oops, it only worked once before giving a new error. The problem seems to have been adding the same printer twice, rather than deleting the old printer before re-adding. The Connection tab should show Local Printer, not Network Printer.

---

