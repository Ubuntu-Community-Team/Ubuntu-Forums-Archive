---
title: "Brother Printer slow, error messages"
date: 2009-01-14
forum: Hardware
---

### Post by Rangi01 on 2009-01-14
Hi all,

I've been having issues with our brother printers, MFC-7820N & MFC-9420CN since upgrading to Intrepid.

Symptoms were...
Sloooowwww printing, it would take ages for even a simple page with text to print, forget graphics.
If you did print graphics it would often just spit out an error message something like "ERROR NAME; range check COMMAND; image OPERAND STACK;".
The page would print above the top of the sheet and the only way of changing it was to scale the page and move the top margin down.

We were using the BRN-3 recommended drivers but after reading elsewhere these don't seem to be compatible so changed over to the CUPS drivers now everything works as they are supposed to.

There is no need to remove the old drivers, that just causes issues.  Simply go to Synaptic, search for 'brother' and then go through each description by clicking on the title until you find your machine, apply the new programme the go to your printer properties and change the driver, you might have to search a bit but it will be your driver name  with CUPS after it, select it complete the wizard and your set. :)

---

### Post by zeroluck on 2009-06-08
Thank you so much. I actually thought the problem was with the network. You saved me a lot of time.

---

