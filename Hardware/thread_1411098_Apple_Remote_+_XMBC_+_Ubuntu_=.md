---
title: "Apple Remote + XMBC + Ubuntu = ?"
date: 2010-02-19
forum: Hardware
---

### Post by Xero Xenith on 2010-02-19
Hey all, been trying for a while to get this working. Ubuntu Karmic 9.10 64-bit on a PC.

I have here an Apple Remote that came with a ~2007 MacBook (it works, no issue there), along with a "Philips eHome Infrared Receiver" that has a little red LED that comes on when I press something on the remote.

My problem is getting that signal to Ubuntu and XBMC - and I'm lost.

lsusb - 
```
Bus 001 Device 013: ID 1267:02f0 Logic3 / SpectraVideo plc 
Bus 001 Device 012: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 011: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 001 Device 010: ID 050d:706a Belkin Components 
Bus 001 Device 009: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 007: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 005: ID 0bc2:3001 Seagate RSS LLC 
Bus 001 Device 004: ID 0d49:3200 Maxtor 
Bus 001 Device 002: ID 050d:0706 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 009: ID 0471:0815 Philips eHome Infrared Receiver
Bus 002 Device 008: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 005: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 002 Device 006: ID 06a3:0107 Saitek PLC 
Bus 002 Device 007: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And here's the output of cat '/proc/bus/input/devices'.
[http://pastebin.com/f2e76a7aa](http://pastebin.com/f2e76a7aa)

I can't seem to find the receiver in there - perhaps that's why irw doesn't work, just throwing back "connect: No such file or directory".

Any ideas, tutorials or anything here would be extremely useful! :)

---

