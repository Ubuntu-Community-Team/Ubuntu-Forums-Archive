---
title: "Any limitation in the USB to serial Ports--ttyUSB"
date: 2016-01-19
forum: Hardware
---

### Post by P_S_Reddy on 2016-01-19
Hi,
I am trying to connect my LTE modems to a ubuntu machine through a USB HUB.In these case I am connecting 8 LTE modem to the PC by cascading USB hubs.
Each LTE modem driver has 6 USB instances over all i am able to connect only 4 modems
Is there any limitation in ubuntu regrading the No of USB ports\

With Regards
P S Reddy

---

### Post by Nuno_Abreu on 2016-01-22
Cascading USB hubs should be no problem, regardless of the OS used.

Just keep in mind that hubs share the power from the root hub, that is, you might not get enough power to make it functional - but I believe that's not true in your case, it might just reduce the throughput speed and latency.

Hope this helps.

---

### Post by deadflowr on 2016-01-22
Moved to *Hardware*

---

