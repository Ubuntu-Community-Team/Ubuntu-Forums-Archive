---
title: "USB Mouse not automatically recognized"
date: 2010-11-17
forum: Hardware
---

### Post by jjjjeremy on 2010-11-17
I plugged in my USB mouse into my laptop today, and Ubuntu isn't recognizing it in any of my USB slots. It works on my desktop and other laptop, and when I plug it in it lights up, but I get no response at all. 

lshw gives ```
           *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:50a0(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:94705c00-94705fff
 
     *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5080(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5060(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5040(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:94705800-94705bff

```

The funny thing about lshw is that I only have 3 usb slots.
I've also been messing around with my wireless drivers, maybe I deleted / blacklisted the driver for the mouse?

---

### Post by oldfred on 2010-11-17
Did you also check BIOS? It often has an enable USB mouse & keyboard setting.

---

### Post by jjjjeremy on 2010-11-17
> **oldfred said:**
> Did you also check BIOS? It often has an enable USB mouse & keyboard setting.

Didn't see anything. That's the first time I had looked at my BIOS, and was surprised to see how bare it was.

---

### Post by oldfred on 2010-11-17
Desktops tend to have a lot more settings.

try this:

Plug in mouse and then see what message you get:

dmesg | tail -n 20

---

### Post by jjjjeremy on 2010-11-17
```
 dmesg | tail -n 20 
``` 

gives

```

[   18.059468] ppdev: user-space parallel port driver
[   28.490031] eth1: no IPv6 routers present
[   48.563316] lo: Disabled Privacy Extensions
[ 1036.661855] lo: Disabled Privacy Extensions
[ 1054.122088] lo: Disabled Privacy Extensions
[ 2580.545552] __ratelimit: 15 callbacks suppressed
[ 2580.545557] npviewer.bin[2121]: segfault at 0 ip 00000000f6197db1 sp 00000000ffdbbf20 error 4 in libflashplayer.so[f5df9000+b2c000]
[ 3066.506646] lo: Disabled Privacy Extensions
[ 3702.600734] lo: Disabled Privacy Extensions
[ 7356.220027] usb 2-1: new high speed USB device using ehci_hcd and address 2
[ 7356.374866] usb 2-1: configuration #1 chosen from 3 choices
[ 8222.130018] usb 8-1: new low speed USB device using uhci_hcd and address 2
[ 8222.307154] usb 8-1: configuration #1 chosen from 1 choice
[ 8222.790111] usb 8-1: USB disconnect, address 2
[ 8223.820031] usb 8-1: new low speed USB device using uhci_hcd and address 3
[ 8223.998171] usb 8-1: configuration #1 chosen from 1 choice
[ 8224.290068] usb 8-1: USB disconnect, address 3
[ 8225.320028] usb 8-1: new low speed USB device using uhci_hcd and address 4
[ 8225.497164] usb 8-1: configuration #1 chosen from 1 choice
[ 8246.301279] usb 2-1: USB disconnect, address 2


```

---

### Post by oldfred on 2010-11-17
My little wireless mouse just works. I do not know enough more to help on USB devices.

```
Nov 14 21:18:38 fred-laptop kernel: [    2.691275] usb 4-1: configuration #1 chosen from 1 choice
Nov 14 21:18:38 fred-laptop kernel: [    2.709117] usbcore: registered new interface driver hiddev
Nov 14 21:18:38 fred-laptop kernel: [    2.724611] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6
Nov 14 21:18:38 fred-laptop kernel: [    2.724710] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1/input0
Nov 14 21:18:38 fred-laptop kernel: [    2.738280] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1/input1
Nov 14 21:18:38 fred-laptop kernel: [    2.738312] usbcore: registered new interface driver usbhid

```

---

