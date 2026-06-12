---
title: "SCSI/SATA controller ordering"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by KnottyMan on 2005-06-08
Trying to install 5.04 on a box with a 3Ware 8506 controller and a Promise S150 controller.  I have the cards placed so the 3Ware inits first in the BIOS.  However, when the kernel boots, it finds the Promise first.  In 2.4 there was a scsihosts=module:module:... ordering parameter, but in 2.6 it looks like it's not there anymore.

How can I get the 3Ware to init first/be SCSI0?  I'd rather install the machine with all it's parts installed.  I suppose I could yank the Promise, install Ubuntu, then reinstall the Promise later after I have modules.conf straight.  But if I ever link into the kernel both drivers, I'm going to get a can't find root fs...

---

### Post by alastair on 2005-06-08
I see what you mean. The "scsihosts" parameter is listed in "kernel-parameters.txt" but does not appear to be used ....

You could try swapping the cards - i.e. switch the PCI slots.

---

