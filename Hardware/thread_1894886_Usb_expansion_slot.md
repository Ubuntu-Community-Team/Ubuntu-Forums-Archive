---
title: "Usb expansion slot"
date: 2011-12-13
forum: Hardware
---

### Post by Manucho on 2011-12-13
Hello to the forums.

I just bought 5 new usb slots, in pci card form.

Installed the card in the system, but ubuntu does not seem to recognize it.

the adapter has a nec chip:

D720101F1

Im wondering how to enable this adaptor. if there is a driver i must add to the system or somethine else.

thanks in advance.

PD: i have already reinstalled ubuntu 10.04 lts and run the updates, and the adapter still does not work.

---

### Post by Manucho on 2011-12-13
After some googling i found this post could be related.

[http://askubuntu.com/questions/55751/in-10-10-usb-3-0-pci-express-card-recognized-by-lspci-but-not-lsusb-or-dmesg](http://askubuntu.com/questions/55751/in-10-10-usb-3-0-pci-express-card-recognized-by-lspci-but-not-lsusb-or-dmesg)

the solution here was to enable usb 3 host side of something like this. (how do i do this in my system).

i will post some results of what i get in my system

```
debora@debora-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
    Subsystem: IBM Device 01e2
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: feb00000-febfffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02) (prog-if 80 [Master])
    Subsystem: IBM Device 01c6
    Flags: bus master, medium devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fff0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
    Subsystem: IBM Device 01c6
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fb00 [size=32]
    Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
    Subsystem: IBM Device 01c6
    Flags: medium devsel, IRQ 9
    I/O ports at fe00 [size=16]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
    Subsystem: IBM Device 01c6
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at f000 [size=256]
    I/O ports at f400 [size=64]
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
    Subsystem: IBM Device 01ce
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 78c0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

01:0d.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
    Subsystem: DTK Computer Device 0105
    Flags: medium devsel, IRQ 21
    Memory at <ignored> (32-bit, non-prefetchable)
    Capabilities: <access denied>

01:0d.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
    Subsystem: DTK Computer Device 0105
    Flags: medium devsel, IRQ 22
    Memory at <ignored> (32-bit, non-prefetchable)
    Capabilities: <access denied>

01:0d.2 USB Controller: NEC Corporation Device 00a0 (rev 04) (prog-if 20)
    Subsystem: DTK Computer Device 0205
    Flags: medium devsel, IRQ 23
    Memory at <ignored> (32-bit, non-prefetchable)
    Capabilities: <access denied>

``````
debora@debora-desktop:~$ lsusb
Bus 001 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

im not sure what does this mean, nor what to do next. any good help is appreciated.

---

### Post by 73ckn797 on 2011-12-13
Are there any BIOS settings to enable system recognition of the PCI slots?

---

### Post by Manucho on 2011-12-14
Now i changed the nec adapter by a via adapter:

the result is almost the same, i still cant get the usb ports working


```
debora@debora-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
    Subsystem: IBM Device 01e2
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: feb00000-febfffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02) (prog-if 80 [Master])
    Subsystem: IBM Device 01c6
    Flags: bus master, medium devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fff0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
    Subsystem: IBM Device 01c6
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fb00 [size=32]
    Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
    Subsystem: IBM Device 01c6
    Flags: medium devsel, IRQ 9
    I/O ports at fe00 [size=16]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
    Subsystem: IBM Device 01c6
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at f000 [size=256]
    I/O ports at f400 [size=64]
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
    Subsystem: IBM Device 01ce
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 78c0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

01:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at 7880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

01:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 22
    I/O ports at 78a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

01:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 23
    Memory at febfef00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

```



```
debora@debora-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

However with the via adapter, seems to be more ports recognized.

still ubuntu wont mount anything.


i will look if there is some BIOS switch or something but i doubt it.

---

