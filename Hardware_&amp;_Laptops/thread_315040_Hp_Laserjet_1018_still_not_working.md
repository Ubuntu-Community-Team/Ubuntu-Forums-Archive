---
title: "Hp Laserjet 1018 still not working"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by erbedo on 2006-12-08
Hi all
     i've just bought a HP LaserJet 1018.
Plugged in the printer and followed the instructions on [http://foo2zjs.rkkda.com/INSTALL]("http://foo2zjs.rkkda.com/INSTALL"), but can't have it working.

This is tail /var/log/messages when i plug it in:
```
Dec  8 19:58:50 harry kernel: usb 2-3: configuration #1 chosen from 1 choice
Dec  8 19:58:50 harry kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
Dec  8 19:58:51 harry /etc/hotplug/usb/hplj1018: loading HP LaserJet 1018 firmware /usr/share/foo2zjs/firmware/sihp1018.dl to /dev/usb/lp0 ...
Dec  8 19:58:51 harry /etc/hotplug/usb/hplj1018: ... download successful.
Dec  8 19:59:10 harry hpiod: removing usblp driver interface=0 for hp:/usb/HP_LaserJet_1018?serial=KP11CQ0 io/hpiod/device.cpp 504
Dec  8 19:59:10 harry kernel: drivers/usb/class/usblp.c: usblp0: removed

```

And this is dmesg:
```
usb 2-3: new high speed USB device using ehci_hcd and address 9
usb 2-3: configuration #1 chosen from 1 choice
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
drivers/usb/class/usblp.c: usblp0: removed
ppdev0: registered pardevice
ppdev0: unregistered pardevice
ppdev0: registered pardevice

```

test page seems ok but nothing it's printed.

Any ideas?

---

