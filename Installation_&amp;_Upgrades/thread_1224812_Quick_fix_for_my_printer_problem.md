---
title: "Quick fix for my printer problem"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Ritzbitts on 2009-07-27
Alright, so, I foundout Lexmark released a driver for my X2690 3-in-1, and went to install it today. For some reason, when I run the wizard, I'm told my CUPS must be at least 1.2, yet I'm running 1.3. I assume this is just a bug in their script.

My next step was to install the printer manually through CUPS via localhost:631. This works fine until I'm prompted o select a PPD file. The Lexmark documentation claims the PPD is located in /usr/lexinkjet/lxk08/etc/lx2600.ppd, yet those directories don't exist. I've searched and searched online for the file, to no avail.

All I need to solve this, I believe, is the PPD file. If anyone out there has a copy or knows where I can locate one, I would be most appreciative. Alternatively, if anyone knows how I can go about extracting the individual file from "lexmark-inkjet-08-driver-1.0-1.i386.deb.sh," that would also be appreciated.

Thanks in advance for all your help, and please feel free to inform me of anything you think I should know, or ask me for more information about my system. I'm running 8.04 on an Acer Aspire 5100-5023. Thanks!

-Josh

---

