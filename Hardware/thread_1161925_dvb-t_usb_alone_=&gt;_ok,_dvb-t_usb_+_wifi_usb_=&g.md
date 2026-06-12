---
title: "dvb-t usb alone =&gt; ok, dvb-t usb + wifi usb =&gt; bad.  Problem with sb700?"
date: 2009-05-17
forum: Hardware
---

### Post by juju27 on 2009-05-17
Hello, 

Recently I build up a  mediacenter with a gigabyte ma78GM-US2H mother board and a AMD Athlon(tm) Dual Core Processor 4850e, 2GB ram. The linux distrib is ubuntu 9.04.

When I plug a DVB-T USB stick (inFast DTV Dongle) alone on the mother board, the dvb-t stick works perfectly.
But now when I also plug the WIFI stick (RT2500), the TV image becomes bad, as if there were some USB data that are lost. The same behaviour occurs when the wifi usb dongle is replaced by a usb hard drive for instance.
Despite the fact the TV recepetion is bad, no errors appears on dmesg.
I should say that the usb sticks are directly plugged on the back of the mother board.

Is it a problem with the SB700 southbridge ?
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

Is it usual that both devices are on the same usb bus whereas they are on two different usb connectors?

I don't know what test should I perform to isolate the problem.
Thanks


juju27

---

### Post by black_shadow on 2009-05-17
Hello

It could be that both of them are taking the limit of the USB power and could if this is the case destroy your PC/Laptop.

Also when using both are you relying on the ariel that came with the DVB-T usb stick if so then it could also be interferance from the Wifi that is causing the issue.

Mike

---

### Post by juju27 on 2009-05-18
Thanks for the comments.
A moment, I was also thinking that it was due to interferences with WIFI waves, but first I am plugged to a roof antenna, but mostly because it is also the case when I replace the wifi stick by a USB hard drive.
About the power leak, I will be a little bit suprized that is due to that  because the TNT stick  sink 500mA and the WIFI one, 300mA. There are up to 12 usb ports on the motherboard, so, if usb fails with only 2 usb, that means there is a problem with usb conception.

Regards.

juju27

---

### Post by juju27 on 2009-05-18
One more hints,

Tonight, I plugged a usb memory key. The dvb-t image became very bad when I was copying large files from the key to the computer. So from this observation, I think we can deduce two things :
- It is not linked to a power supply problem, because a usb memory takes only a small power
- It is definitively not due to interferences between WIFI and TV.

From my point of view, it looks like, the dvb-t stick and memory stick share the SAME hub, and therefore the bandiwth is limited. Consequently, when the data are transfered for the memory stick, dvb-t data are lost.

Does anyone observe the kind of behavior with a sb700 south-bridge?

As I said in the first message, the strange thing is that all the USB2 devices shares the same BUS (BUS 1). But maybe a bus is equivalent to a hub. So It may explain the limited bandwith.
See
Bus 001 Device 007: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 002: ID 0413:6026 Leadtek Research, Inc. WinFast DTV Dongle (warm state)


Does anyone know if it is possible to change the Bus assignation to a usb device? If yes how to do that?

Cheers

juju27

---

