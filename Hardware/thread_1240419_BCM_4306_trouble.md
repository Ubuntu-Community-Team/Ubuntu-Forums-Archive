---
title: "BCM 4306 trouble"
date: 2009-08-14
forum: Hardware
---

### Post by burnclouds on 2009-08-14
I have a d600 from dell I just installed ubuntu9.04 and have activated the b43 driver. I checked and the driver included a firmware. I installed wicd and tried to connect to my AP to no avail. I then updated the firmware for my BCM4306 rev 3. and tried to connect again no joy.

I've read that the D600 has an option in the bios that can sometimes be set to disable the wireless. I have checked and the wireless is enabled. I can preform a "iwlist wlan0 scan" and see a list APs.

Any ideas?

---

### Post by burnclouds on 2009-08-15
Ok so I'm a moron. It help's if MAC address filtering on the AP is off or has the new laptop in the allowed list.

---

