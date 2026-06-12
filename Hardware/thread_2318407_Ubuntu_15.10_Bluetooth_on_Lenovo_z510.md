---
title: "Ubuntu 15.10 Bluetooth on Lenovo z510"
date: 2016-03-25
forum: Hardware
---

### Post by paarthri on 2016-03-25
I cannot get Bluetooth to work on my laptop.

Here are some (hopefully) useful commands:

lsusb:```
Bus 004 Device 002: ID 8087:8000 Intel Corp. Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 007: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 006: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 004: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 003: ID 5986:029d Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

service bluetooth status:```
&#9679; bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2016-03-25 18:43:52 EDT; 7min ago
     Docs: man:bluetoothd(8)
 Main PID: 940 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;940 /usr/lib/bluetooth/bluetoothd


Mar 25 18:43:52 paarths-computer systemd[1]: Starting Bluetooth service...
Mar 25 18:43:52 paarths-computer bluetoothd[940]: Bluetooth daemon 5.35
Mar 25 18:43:52 paarths-computer bluetoothd[940]: Starting SDP server
Mar 25 18:43:52 paarths-computer bluetoothd[940]: Bluetooth management interface 1.10 initialized
Mar 25 18:43:52 paarths-computer systemd[1]: Started Bluetooth service.

```

Thanks is advance!

---

### Post by jeremy31 on 2016-03-26
Post ```
rfkill list all; dmesg | egrep -i 'blue|firm'
```
It should be supported, might just need firmware

---

