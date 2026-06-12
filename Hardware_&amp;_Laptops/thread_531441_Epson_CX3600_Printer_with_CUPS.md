---
title: "Epson CX3600 Printer with CUPS"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by Tim Sawyer on 2007-08-21
I've got an Epson CX3600 hooked up to Ubuntu via a USB cable.  CUPS has found it, and it's installed

However, whenever I print a test page, or send a job to it, the job shows up in cups as "completed" yet nothing ever happened on the printer - no printing, no whirring, no nothing!

This command:

sudo escputil -i -r /dev/usblp0

successfully shows me the ink level, so it's definitely connected fine.  Sounds like a cups problem?  There's nothing obvious in the cups logs.

Can someone shove me in the right direction please?  I can't think of where to starting looking.

Thanks,

Tim.

---

