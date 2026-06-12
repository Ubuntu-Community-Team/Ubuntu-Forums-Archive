---
title: "Logitech M305 Wireless Mouse Not Recognized"
date: 2012-09-05
forum: Hardware
---

### Post by dlpittman on 2012-09-05
I recently converted to ubuntu.  I'm running ubuntu 12.04 on a Dell Latitude D420 laptop.  I'm getting no response from my Logitech M 305 Wireless mouse.  I've checked the forums but haven't uncovered a fix.  ...Little help please.

---

### Post by cortman on 2012-09-05
> **dlpittman said:**
> I recently converted to ubuntu.  I'm running ubuntu 12.04 on a Dell Latitude D420 laptop.  I'm getting no response from my Logitech M 305 Wireless mouse.  I've checked the forums but haven't uncovered a fix.  ...Little help please.

Do you know if that USB port works?
Run

```
lsusb
```

and post output.

---

### Post by dlpittman on 2012-09-09
Here's what i get.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader

---

### Post by cortman on 2012-09-09
> **dlpittman said:**
> Here's what i get.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader

And this is the output with the wireless adapter **plugged in**?

---

### Post by dlpittman on 2012-09-10
Yes

---

### Post by cortman on 2012-09-10
Basic question, but have you tried plugging it into any other ports?

---

