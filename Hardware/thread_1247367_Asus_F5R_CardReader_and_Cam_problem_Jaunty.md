---
title: "Asus F5R CardReader and Cam problem Jaunty"
date: 2009-08-22
forum: Hardware
---

### Post by Senad.Ibraimoski on 2009-08-22
Hi,
I have been using Ubuntu for one year now. 
My built in SD CardReader on my laptop ( Asus F5R ) was working fine on Hardy.Same applies for my built in camera. Now I migrated to Jaunty and I have two major problems:
[LIST=1]
[*]Camera Not working
[*]CardReader Not working
[/LIST]
I tried number of things but nothing can't seem to get hold of the problem.
I've tried some things:
```

sudo mkdir /media/flash1
sudo mount /dev/sda1 /media/flash1
//or
modprobe tifm_sd
...
...

```

Here is my lspci:

```

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fa800000-fa8fffff
	Prefetchable memory behind bridge: aff00000-bfefffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fa900000-fa9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: faa00000-fe9fffff
	Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at e800 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at d800 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 82 [Master PriP])
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 1339
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: ASUSTeK Computer Inc. Device 1417
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
	Subsystem: ASUSTeK Computer Inc. Device 1402
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at b0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9800 [size=256]
	Memory at fa8f0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fa8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 170f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa9fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb

06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device 1415
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at feac0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at feaa0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: atl2
	Kernel modules: atl2


```

I would be **very** gratefull if someone could help me.
Best Regards,
S.I

---

