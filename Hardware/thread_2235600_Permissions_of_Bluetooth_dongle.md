---
title: "Permissions of Bluetooth dongle"
date: 2014-07-22
forum: Hardware
---

### Post by nikkila-vesa on 2014-07-22
I have usb BLE dongle attached to my computer but using it requires superuser rights. For example, I can't do ```
hcitool lescan
``` without sudo, or I get ```
Set scan parameters failed: Operation not permitted
```. However, I can do normal scan (not low energy) without any rights: ```
hcitool scan
```.

This is what lsusb shows:
```
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

I tried to modify rules.d folder and add this to file ```
50-ble_dongle.rules
```:
```

SUBSYSTEM!="usb", ACTION!="add", GOTO="dongle_rules_end"
ATTRS{idVendor}=="0a12", ATTRS{idProduct}=="0001", MODE="0666", OWNER="vesa", GROUP="root"
LABEL="dongle_rules_end"

```

I have no idea if I did it right.

Thank you for the answer!

 - Vesa

---

