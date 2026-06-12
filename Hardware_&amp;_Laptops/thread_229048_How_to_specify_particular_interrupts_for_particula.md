---
title: "How to specify particular interrupts for particular modules?"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by crashtestyyz on 2006-08-03
I have an ethernet card which seems to be sharing an interrupt (185) with *something* else.  where dmesg shows 4 lines concerning the card, the driver, the interrupt used, that interrupt number shows up again in dmesg a little while later, but no other details are attached to it.

I've managed to build a RAID 5 server, and now am at an incredibly frustrating impasse where I can't actually transfer any data to it.  After a short amount of time, the ethernet dies and I have to restart network services.  ](*,) :confused: 

I've spent hours and hours and hours gutting the init.d, the inittab, rc*.d, blacklisted stuff (which in some cases just comes back anyway - notably hotplug modules)..   I'd actually PAY somebody to come fix this at this point (in beer).

Any help or suggestions would be greatly appreciated.

Christopher

---

### Post by crashtestyyz on 2006-08-04
<crickets>

---

