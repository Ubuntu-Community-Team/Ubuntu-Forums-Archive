---
title: "Bluetoot devices discovered,  but not their service"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by cyberco on 2007-09-16
- Feisty
- Zoom 4312 Bluetooth PC-Card
 
Using hcitool (or pybluez) I can get a proper list of all bluetooth divices in my neighborhood, but I am unable to list services for a device. The sdptool and PyBluez don't list anything. In Windows XP using PyBluez (the python module for bluetooth devices) the services are listed just fine.

Listing the SDP records does work using the following command, though:

sdptool records 00:03:C9:08:02:9B

---

