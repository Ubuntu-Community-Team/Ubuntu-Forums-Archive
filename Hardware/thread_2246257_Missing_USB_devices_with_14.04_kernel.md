---
title: "Missing USB devices with 14.04 kernel"
date: 2014-09-29
forum: Hardware
---

### Post by Stephen_Byrne on 2014-09-29
I have an industrial computer based on Intel SCH Poulsbo. With an Ubuntu 9.04 install from the manufacturer, lsusb -t shows (with my comments in parenthesis):

```

Bus#  1
`-Dev#   1 Vendor 0x1d6b Product 0x0002       (Linux : hub)
  |-Dev#   2 Vendor 0x1a40 Product 0x0101     (Terminus : hub)
  `-Dev#   5 Vendor 0x04cc Product 0x1520     (Philips : hub)
    |-Dev#   6 Vendor 0x1546 Product 0x01a5   (u-blox AG : u-blox 5)
    `-Dev#   7 Vendor 0x0403 Product 0x6011   (FTDI : Quad RS232-HS)
Bus#  2
`-Dev#   1 Vendor 0x1d6b Product 0x0001       (Linux : hub)
Bus#  3
`-Dev#   1 Vendor 0x1d6b Product 0x0001       (Linux : hub)
  `-Dev#   2 Vendor 0x03f0 Product 0x0024     (HP : KU-0316 Keyboard)
Bus#  4
`-Dev#   1 Vendor 0x1d6b Product 0x0001       (Linux : hub)

```

With 14.04, lusb -t shows:

```

/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M   (Linux : hub)
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M   (Linux : hub)
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M   ( keyboard)
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M   (Linux : hub)
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M  (mouse)
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/8p, 480M  (Linux : hub)
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M  (Terminus : hub)

```

The Philips hub (0x04cc:t 0x1520) does not show up.

lspci shows the root hub:

```

00:1d.7 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
        Subsystem: Device 8100:8086
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Kernel driver in use: ehci-pci

```

Is that the Philips hub does not show up a problem with the driver for the Poulsbo USB EHCI system controller hub or the driver for the Philips hub itself?

---

### Post by Stephen_Byrne on 2014-10-13
Driver did not see the Philips hub. BIOS update from manufacturer fixed it.

---

