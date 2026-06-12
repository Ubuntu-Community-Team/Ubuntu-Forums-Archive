---
title: "g_serial module problems with 5.3.0-40 kernel"
date: 2020-03-12
forum: Hardware
---

### Post by colker on 2020-03-12
Hi all. This is my first post. I have a computer with an OTG port running Ubuntu 18.04 that is acting as a Device connected to another computer running Ubuntu 18.04 (Host). I'm using the g_serial module to enable communications using the OTG port. Communications work fine if the Device has kernel 5.3.0-28. However, when I upgraded to 5.3.0-40 kernel, the communication is only one way. That is, the Device can send to the Host and the Host receives it fine, but whatever I send from the Host to Device is not received by the Device.

I downgraded the kernel to 5.3.0-28 and two-way communication is working again. That is, the Host receives what the Device sends and the Device receives what the Host sends.

Does anyone have any ideas as to what could be causing two-way communication to break after upgrading the kernel?

Thanks,

Colin

---

