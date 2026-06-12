---
title: "SATA150 SX4 - Module &quot;sata-sx4&quot; missing?"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by forbjok on 2009-10-06
I'm trying to install Ubuntu Server 9.04 x86 (because unfortunately the machine is a bit old and doesn't have an x86-64 cpu) on a HP ProLiant ML110 server.

It has what appears to be a Promise FastTrak S150 SX4 SATA raid adapter.

When I boot the Ubuntu Server CD, everything seems to go fine until it gets to the point where it tries to detect the harddrives and fails. Apparently it hasn't got a driver loaded for the SATA card, and asks if I want to select one, then displays a list of modules to select from - none of which appear to have anything to do with SATA whatsoever.

The information revealed by Google on the subject, seems to indicate that this particular type of card should be supported in the Linux kernel for several years now, through a module called "sata_sx4".

After opening up a console from the Ubuntu installer, I look in /lib/modules to see if there are any useful modules, but I can't find "sata_sx4" anywhere in there. In fact, the only thing I found at all that seems to have anything to do with SATA at all is a module called "sata_mv", which according to Google is a driver for a different type of SATA controller.

Why is "sata_sx4" missing from the install CD? Has it been renamed something else? If so, what?
Is there any sane way to get this to work without replacing the SATA controller?

UPDATE:
I replaced the original S150 SX4 controller with a new Promise SATA300 TX4 controller instead, which worked immediately.
I guess the new one is faster anyway, so it was probably just as well to replace it.

I'd still like to know why the S150 SX4 isn't supported on the Ubuntu CD though, if anyone knows.
Maybe the sata_sx4 module is built into the kernel, but doesn't support this particular chip?

---

