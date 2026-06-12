---
title: "Network adaptor will not connect to 1000Mbit switch"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by richo132 on 2008-03-03
When connected to a 100Mbit switch (Linksys SD208), my Linksys eg1032v3 NIC is correctly detected and apparently works properly with either the r8169 or eg1032v3 driver.
If I connect the NIC directly to a 1000Mbit switch (Linksys SD2008), the NIC doesn't work.
When connected to the 1000Mbit switch, a LED on the NIC lights up on a cold boot, but goes out when boot reaches the udev stage.
If the NIC is connected to the 1000Mbit switch via the 100Mbit switch, everything works fine.
In other words:
network > 1000Mbit SW > 100 Mbit SW > eg1032v3 eg1032v3 works fine
network > 1000Mbit SW > eg1032v3 eg1032v3 doesn't work
As far as I can tell the 2 switches perform correctly with other attached devices.
When attached to 1000Mbit SW and rebooted, the PC correctly identifies the NIC, maps it to eth0 and loads the driver. However, eth0 does not come up.
Any suggestions on how to fix or further diagnose this problem ?

---

