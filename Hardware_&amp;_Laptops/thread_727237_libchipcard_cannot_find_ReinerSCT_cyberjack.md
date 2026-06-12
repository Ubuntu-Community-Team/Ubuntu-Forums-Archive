---
title: "libchipcard cannot find ReinerSCT cyberjack"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by QNo on 2008-03-17
Hi,

Kubuntu 7.10

Hardware 0c4b:0300 Reiner SCT Kartensysteme GmbH cyberJack pinpad(a) found by lsusb.

Command "cyberjack" finds reader, user is in group "cyberjack", "all found readers are ready".

But chipcard3-tool list or chipcard3-tool check gives no output. In syslog: 
Mar 17 21:10:08 multi chipcardd[8290]: clr_clientready.c:  104: Client "47dece39" started (chipcard3-tool, Gwen 2.6.1-stable-r0, ChipCard 3.0.3.0stable)
Mar 17 21:10:08 multi chipcardd[8290]: clr_notification.c:  540: Client 47dece39: SetNotify [chipcard3-tool/nobody]
Mar 17 21:10:08 multi chipcardd[8290]: cs_callbacks.c:   33: One of my connections is down. Don't worry just yet, this might be ok...
Mar 17 21:10:08 multi chipcardd[8290]: clientmanager.c:  398: Removing client 47dece39 [chipcard3-tool/nobody]

Also, no application can access the cardreader. What's going wrong?

---

