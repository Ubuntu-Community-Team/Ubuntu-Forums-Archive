---
title: "Multiple Grub errors affected by USB periferials!!!"
date: 2010-01-18
forum: Hardware
---

### Post by Pavel.Niedoba on 2010-01-18
I have very strange behavior on my Thinkpad t60. It is dual boot system with grub and it boots just fine when there is no USB hub plugged in. I have 2 USB hubs 4 ports each. 

Here is full list:

Bus 001 Device 017: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 016: ID 03f0:4607 Hewlett-Packard 
Bus 001 Device 006: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 005: ID 0458:000e KYE Systems Corp. (Mouse Systems) VideoCAM Web
Bus 001 Device 004: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I try to boot with both hubs connected, the grub will freeze in stage 1.5. Error is displayed but no number follows. At this point Atl+Ctrl+Del does nothing, only hard power off can. I tried different combination of hubs / periferials and I got multiple errors (1,17,25) in stage 1.5.  Some combination will make Grub to auto reboot forever.  When I disconnect both hubs it will boot fine. I did grub-install, no change. Critical periferials are Cannon LIDO scanner and i560 printer. There is easy work around, but Ubuntu is better than that.

---

### Post by PRC09 on 2010-02-05
Sounds as if your machine is trying to boot from usb.Check bios and see what your boot order is.....

---

### Post by Pavel.Niedoba on 2010-02-27
Full reinstall of the system solved that problem, reinstall of grub didn't

---

