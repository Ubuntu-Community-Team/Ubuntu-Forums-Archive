---
title: "Bluetooth dongle (DBT-120 A2) and 7.10 on Portege M200"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by ZeeG on 2007-12-05
I have installed 7.10 on my Portege M200 laptop and plug a usb bluetooth dongle (DBT-120 A2)
When I check the list of usb devices, I see followings:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
Bus 001 Device 001: ID 0000:0000  

However, if I scan the device, using "hcitool scan" or "sudo hciconfig hci0"
I'm getting a message that says "Device is not available: No such device"
I don't see tray icon for bluetooth, either.

---

