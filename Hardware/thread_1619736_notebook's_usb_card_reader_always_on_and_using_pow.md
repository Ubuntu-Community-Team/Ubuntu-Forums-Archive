---
title: "notebook's usb card reader always on and using power"
date: 2010-11-12
forum: Hardware
---

### Post by Axx83 on 2010-11-12
Hi guys. I have an Acer Travelmate 8172t with Maverick installed.

There is a card reader which is always on and uses power as powertop suggests:
```
Statistiche di sospensione di recenti USB
Nome del dispositivo attivo
100,0%	Dispositivo USB 2-1.6 : USB2.0-CRW (Generic)
  0,0%	Dispositivo USB 1-1.2 : 1.3M WebCam (Suyin)
  0,0%	Dispositivo USB 1-1.4 : Fingerprint Sensor ()
100,0%	/sys/bus/usb/devices/2-1
  0,0%	/sys/bus/usb/devices/1-1
100,0%	Dispositivo USB usb2 : EHCI Host Controller (Linux 2.6.35-22-generic ehci_hcd)
  0,0%	Dispositivo USB usb1 : EHCI Host Controller (Linux 2.6.35-22-generic ehci_hcd)
```

this is the result of lsusb:
```
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 064e:a219 Suyin Corp. 
Bus 001 Device 004: ID 08ff:168c AuthenTec, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The reader should be the realtek device. Currently on my pc I have a script that puts usb ports to suspension if not used and that's why all the other devices are turned off. This one is not tough.

How can I effectively turn it off? Could I permanently disable it as I never actually use it ?

Thank you.

---

### Post by Axx83 on 2010-11-12
After a bit of tinkering I found that removing usb_storage module effectively turns off the card reader, is this module only used for card reader or also for other devices?

---

