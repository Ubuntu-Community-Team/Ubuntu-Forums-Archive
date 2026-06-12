---
title: "Problems with external HD"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by Pino_ptrs on 2007-09-25
I just bought a new usb hard-drive enclosure (Cooler Master) and hard-drive (Western Digital Caviar SE16 320GB SATA) but I'm having problems getting it to work in Ubuntu (in Windows it works just fine).

When I plug it in and type lsusb in the terminal it results in:

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
(The computer doesn't recognize it)

When I type dmesg in the terminal it results in:

```
[ 1442.984000] usb 3-1: device descriptor read/64, error -110
[ 1448.200000] usb 3-1: device descriptor read/64, error -32
[ 1448.416000] usb 3-1: new high speed USB device using ehci_hcd and address 16
[ 1448.528000] usb 3-1: device descriptor read/64, error -32
[ 1448.744000] usb 3-1: device descriptor read/64, error -32
[ 1448.960000] usb 3-1: new high speed USB device using ehci_hcd and address 17
```

Is anyone experiencing the same problem? And does anyone know a solution to my problem?

Thanx anyway!!

---

