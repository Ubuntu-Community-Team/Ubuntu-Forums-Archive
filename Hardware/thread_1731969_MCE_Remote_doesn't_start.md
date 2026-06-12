---
title: "MCE Remote doesn't start"
date: 2011-04-17
forum: Hardware
---

### Post by enderbr on 2011-04-17
My Philips MCE USB IR Remote worked like a charm ever since I installed xubuntu in my current media center desktop. Once I finished installing XBMC and setting everything up I disconnected the USB devices (with the computer turned off) and reconnected just the remote receiver. From then on xubuntu doesn't recognize it anymore (lsusb doesn't show anything) and I actually got it working once by replugging it and running dmesg a couple of times, now not even that works anymore...

My lsusb output:
> Bus 004 Device 003: ID 1c4f:0003 SiGma Micro HID controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:1603 Belkin Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
s

Alright... this one has been puzzling me for a while now and I couldn't find anything to solve it in the forums (tried asking in the ubuntu IRC channel as well). Anyone can offer some insight?

---

