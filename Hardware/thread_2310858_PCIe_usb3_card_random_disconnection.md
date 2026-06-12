---
title: "PCIe usb3 card random disconnection"
date: 2016-01-22
forum: Hardware
---

### Post by matrem on 2016-01-22
Hello,

I recently bought and installed a PCIe usb3 card (fresco logic FL1100EX).
It works great under windows, but under my kubuntu 15.10, it works for a  time and then disconnects my connected usb devices (printer, phone, disk, ...). Then I can't reconnect anything without a reboot.

I there a way for me to understand and perhaps fix this strange behaviour?

---

### Post by matrem on 2016-01-26
Some more information

lspci -v give me this :

[FONT=Courier New][I]02:00.0 USB controller: Fresco Logic FL1100 USB 3.0 Host Controller (rev 01) (prog-if 30 [XHCI])
        Subsystem: Fresco Logic FL1100 USB 3.0 Host Controller
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f3100000 (64-bit, non-prefetchable) [size=64K]
        Memory at f3110000 (64-bit, non-prefetchable) [size=4K]
        Memory at f3111000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd[/I][/FONT]


cat /var/log/syslog | grep xhci give me this :

[FONT=Courier New][I]xhci_hcd 0000:02:00.0: xHCI Host Controller
xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 1
xhci_hcd 0000:02:00.0: hcc params 0x200071a1 hci version 0x100 quirks 0x00000010
usb usb1: Manufacturer: Linux 4.2.0-25-generic xhci-hcd
xhci_hcd 0000:02:00.0: xHCI Host Controller
xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
usb usb2: Manufacturer: Linux 4.2.0-25-generic xhci-hcd
usb 1-3: new high-speed USB device number 2 using xhci_hcd
usb 1-3: new high-speed USB device number 3 using xhci_hcd
usb 1-2: new high-speed USB device number 4 using xhci_hcd
xhci_hcd 0000:02:00.0: xHCI host not responding to stop endpoint command.
xhci_hcd 0000:02:00.0: Assuming host is dying, halting host.
xhci_hcd 0000:02:00.0: HC died; cleaning up[/I][/FONT]

We can see in the end the disconnection

---

### Post by matrem on 2016-02-05
No one have an idea about that ? :)

---

