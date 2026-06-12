---
title: "Onboard Lan stops boot!"
date: 2009-04-12
forum: Hardware
---

### Post by f37u5g0d on 2009-04-12
If I turn off my onboard lan my computer boots fine into ubuntu.  If I turn on my lan I get stuck during the boot at "ata2"  What is going on here?  What can I do to boot the os with the onboard lan turned on so that I can trouble shoot it.

lshw excerpt with onboard lan turned off:

network DISABLED
description: Ethernet interface
physical id: 1
logical name pan0
serial: b9:95:a4:c2:93:64
capabilities: Ethernet physical
config: broadcast = yes driver = bridge driverversion=2.3 firmware = N/A link = yes multicast = yes

I think the firmware on the card is fried as well becuase it doesn't won't let ubuntu work and it doesn't work in windows.

---

### Post by f37u5g0d on 2009-06-02
The hardware was fried.

---

