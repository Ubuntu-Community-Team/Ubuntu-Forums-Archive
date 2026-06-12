---
title: "USB ports stopped working"
date: 2010-07-29
forum: Hardware
---

### Post by shabutaru on 2010-07-29
Hi, I'm running ubuntu version 10.04 ( Lucid Lynx) and out of the blue all my usb ports stopped working.  I've been searching the internet for a solution and the only ones I've found are out dated, and no longer work, or just don't work at all.  Is there any solution other than re-formating?

---

### Post by lidex on 2010-07-31
What is the output of:
```
lsusb
```
```
sudo lshw -C bus
```

---

### Post by darramonde on 2010-08-23
> **lidex said:**
> What is the output of:
```
lsusb
```
```
sudo lshw -C bus
```

I've got the same problem.

**Here's the outcome of sudo lshw -C bus:**

*-core                  
       description: Motherboard
       product: NEC Versa Premium
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 5a
       serial: 12345678
  *-usb:0
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=uhci_hcd latency=22
       resources: irq:11 ioport:1200(size=32)
  *-usb:1
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=uhci_hcd latency=22
       resources: irq:7 ioport:1220(size=32)
  *-usb:2
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=uhci_hcd latency=22
       resources: irq:5 ioport:1240(size=32)
  *-usb:3
       description: USB Controller
       product: USB 2.0
       vendor: VIA Technologies, Inc.
       physical id: 10.3
       bus info: pci@0000:00:10.3
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ehci_hcd latency=22
       resources: irq:10 memory:7c010000-7c0100ff

---

### Post by lidex on 2010-08-23
> **darramonde said:**
> I've got the same problem.



Looks like the hardware is recognized. What about:
```
lsusb
```

---

### Post by darramonde on 2010-08-24
> **lidex said:**
> Looks like the hardware is recognized. What about:
```
lsusb
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by lidex on 2010-08-24
> **darramonde said:**
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Not seeing any connected devices. Is anything plugged into your usb ports?
How about this output:
```
dmesg | grep -C1 -E 'usb|ohci'
```

---

### Post by darramonde on 2010-08-24
> **lidex said:**
> What is the output of:
```
lsusb
```
```
sudo lshw -C bus
```

**Here's the outcome:**

*-core                  
       description: Motherboard
       product: NEC Versa Premium
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 5a
       serial: 12345678
  *-usb:0
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=uhci_hcd latency=22
       resources: irq:11 ioport:1200(size=32)
  *-usb:1
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=uhci_hcd latency=22
       resources: irq:7 ioport:1220(size=32)
  *-usb:2
       description: USB Controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: 80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=uhci_hcd latency=22
       resources: irq:5 ioport:1240(size=32)
  *-usb:3
       description: USB Controller
       product: USB 2.0
       vendor: VIA Technologies, Inc.
       physical id: 10.3
       bus info: pci@0000:00:10.3
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ehci_hcd latency=22
       resources: irq:10 memory:7c010000-7c0100ff

---

