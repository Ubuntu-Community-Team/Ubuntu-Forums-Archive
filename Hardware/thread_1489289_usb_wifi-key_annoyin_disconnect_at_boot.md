---
title: "usb wifi-key annoyin disconnect at boot"
date: 2010-05-20
forum: Hardware
---

### Post by zluspai on 2010-05-20
Dear Ubuntu fans,

I have a problem since 10.4 is up. I have an USB hub where a keyboard, a mouse and a WIFI usb-key is plugged in. What I see is that during the boot the WIFI connect nicely and in 10 seconds it disconnects. The WIFI key disappears from the "lsusb" listing and will only reappear if I unplug/replug that. 

Now when I plug one more device to the same hub; all the devices from that hub disappears from "lsusb" and reappear in few seconds, except the WIFI-key. Only replug helps.

It might be an usb power problem; but if I boot to windows XP everything and all the same works fine. Also I did not have this problem with ubuntu 9.x. Is there any changes on usb 10 which may affect this? Or any ways to configure usb devices initialization/ powering and alike?

lsusb output:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 076b:3021 OmniKey AG CardMan 3121
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 014: ID 0ace:1211 ZyDAS 802.11bg
Bus 002 Device 013: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 012: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 011: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks,
Zoltan

---

