---
title: "Execute a script when a device was detected"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by Nasenbaer on 2007-07-07
Hi, I want to start a script everytime a specific usb device was detected. I think I have to modify the HAL configs for this but I don't exactly know what to do - can someone help me?  P.S.: Had no luck with google search :/

---

### Post by Martje_001 on 2007-07-07
Maby you can make a script that's runs in a loop doing 'lsusb | grep $device'?

---

### Post by Nasenbaer on 2007-07-07
Would be possible but polling is not very nice implementation of such a mechanism. :) Any other ideas?

---

