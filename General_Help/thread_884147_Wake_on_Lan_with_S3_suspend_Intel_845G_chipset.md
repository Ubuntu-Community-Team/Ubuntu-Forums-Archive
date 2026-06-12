---
title: "Wake on Lan with S3 suspend Intel 845G chipset"
date: 2008-08-08
forum: General Help
---

### Post by danielsbrewer on 2008-08-08
I am having a rather frustrating time trying to get Wake on LAN working when the system is in a suspend (S3) state.

Here's what works:
1) Shutting down the computer. Sending a magic packet reboots it.
2) Suspending the computer. The led flashes like it is in suspend. Pressing the power button wakes the machine.

Here's what doesn't work:
1) Suspending the computer. Sending a magic packet doesn't unsuspend it.


The NIC is an intergrated Intel PRO/100 VM Network Connection with WOL using the Intel 845G chipset.  The machine is a Compaq Evo D510 ultra slim desktop which I am using as a server ([http://h18000.www1.hp.com/products/quickspecs/11349_div/11349_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11349_div/11349_div.HTML)).

Has anyone got any ideas how to sort this out?  The options in the BIOS are limited to say the least but I have tried to turn on everything that has a remote possibility of being relevant.

---

