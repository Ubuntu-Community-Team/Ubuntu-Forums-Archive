---
title: "Bluetooth detected but not working iogear gbu211 ubuntu 9.04 64bit"
date: 2009-05-07
forum: Hardware
---

### Post by denisbergeron on 2009-05-07
The Bluetooth IOGear gbu211 is detected as an Broadcom Corp. Bluetooth dongle
```

denis@Bureau-Linux:/proc$ lsusb 
Bus 001 Device 006: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 001 Device 008: ID 04e8:326c Samsung Electronics Co., Ltd ML-2010P Mono Laser Printer
Bus 001 Device 007: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 005: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 002: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 009: ID 0a5c:3503 Broadcom Corp. 
Bus 002 Device 008: ID 0a5c:3502 Broadcom Corp. 
Bus 002 Device 007: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 002 Device 006: ID 0a5c:3500 Broadcom Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
denis@Bureau-Linux:/proc$ 

```
But it's impossible to add a new device neither with gnome or kde interface. 
Eveything worked in 8.11 and 8.4 and...

---

### Post by divague on 2009-05-07
Unplug the dongle, restart the machine and plug the dongle. That worked for me.

---

### Post by denisbergeron on 2009-05-07
> **divague said:**
> Unplug the dongle, restart the machine and plug the dongle. That worked for me.

Doesn't work for me. I try every boot/plug/unplug combinaison.
I unsintall and reinstall every bluez package...

Someone have another idea ?

---

