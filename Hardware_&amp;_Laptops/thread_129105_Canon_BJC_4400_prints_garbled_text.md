---
title: "Canon BJC 4400 prints garbled text"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by tnichols on 2006-02-12
I just setup a new AMD64 system running Ubuntu 64-bit Breezy.  I ma having some issues with printing to my Canon BJC-4400.  I have tried the BJC600 driver (which is recommended) and the gimp-print driver with no luck.  It just prints page after page of garbled text when doing a test page.  Occasionally, instead of printing garbled text, the printer activity light will blink for about 10 seconds and then quit without doing anything.

Does anyone know of any tricks I could try to use to make this work?

-Tim

---

### Post by tnichols on 2006-02-14
I figured it out.  The problem was due to the Parallel Port settings in my motherboard's BIOS.  I have an ASUS A8N-E and the port was set for EPP+ECP, I changed to EPP and it works.

---

