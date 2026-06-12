---
title: "TNT USB + WIFI USB =&gt; PROBLEM with SB700 southbridge (MA78GM-US2H motherboard)"
date: 2009-05-16
forum: Hardware
---

### Post by juju27 on 2009-05-16
Hello, 

When I plug a DVB-T USB dongle (inFast DTV Dongle) alone on a gigabyte ma78GM-US2H mother board, the tnt device works perfec
Butt now when I also plug a WIFI usb (RT2500), the DVB-T image becomes bad, as if there were some USB pacquets lost.  The same behaviour occurs when the wifi usb dongle is replaced by a usb hard drive.
Despite the fact the DVB-T recepetion is bad, no errors appears on dmesg.
The usb dongles are directly pluged on the back of the mother board.

The USB controller is  SB700 (ASUS). 

lsusb gives
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 002: ID 0413:6026 Leadtek Research, Inc. WinFast DTV Dongle (warm state)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Is it usual that both devices are on the same Bus whereas they are on two different usb plug?
My config
Mother board : MA78GM-US2H
Ubuntu 9.04
I must say, I don't know what test should I perform to isolate the problem.
Thanks


juju27

---

