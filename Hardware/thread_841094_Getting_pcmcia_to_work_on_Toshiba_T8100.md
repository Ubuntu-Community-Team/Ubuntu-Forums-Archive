---
title: "Getting pcmcia to work on Toshiba T8100"
date: 2008-06-26
forum: Hardware
---

### Post by firmit on 2008-06-26
I have an old Toshiba Tecra 8100. When installing Ubuntu 7.10, the installer locates my PCMCIA D-Link Fast ethernet card and connects. 

But, why does it not work "out-of-the-box" after the installation is complete? And how on earth do I get it to work? I have google'd the net for hours, and I am getting a bit confused by all the pcmciautils/pcmcia-ps/kernel-integration/grub-editing tips. I need a little howto start and find the pcmcia wireless smc card and d-link dfe-670TXD.

The laptop-testing team says it is working with ubuntu, but says nothing about how to get it to work ( [link]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecra8100?highlight=%28toshiba%29%7C%28tecra%29") ).

What do I do?

---

### Post by firmit on 2008-07-03
Solved
[http://forums.debian.net/viewtopic.php?p=158940#158940](http://forums.debian.net/viewtopic.php?p=158940#158940)

for some reason my pcmcia controller was not loaded in kernel at boot time

---

