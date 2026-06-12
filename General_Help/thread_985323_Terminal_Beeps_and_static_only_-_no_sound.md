---
title: "Terminal Beeps and static only - no sound"
date: 2008-11-17
forum: General Help
---

### Post by jodef on 2008-11-17
I have been troubleshooting my wireless connection in another thread on one of the reboots system stalled at alsa shutdown now I have no sound. It worked flawlessly previously.

**aplay -l**

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``` 

In alsamixer sound is not muted and set at 100% in the terminal I hear the beeps and when attempting to play music I only hear static.

**lspci -v**

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at eff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at efec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0
	Memory at eff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

[B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel[/B]

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: efd00000-efdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efa00000-efcfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: ef900000-ef9fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Device 01cd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Device 01cd
	Flags: medium devsel, IRQ 4
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at ef9fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at ef9fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at ef9fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: Dell Device 01cd
	Flags: medium devsel, IRQ 11
	Memory at ef9fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: Dell Device 01cd
	Flags: medium devsel, IRQ 11
	Memory at ef9fd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
```

Any help would be greatly appreciated.

Thanks.

---

### Post by jodef on 2008-11-17
Ok I did some searching realised it is a known bug in Ibex applied the workaround found in this thread: [http://ubuntuforums.org/showpost.php?p=6099553&postcount=18](http://ubuntuforums.org/showpost.php?p=6099553&postcount=18) however I still haven't been able to get sound working again.

I have tried reinstalling all alsa related stuff and playing around with the settings in the Sound GUI however when I hit test it locks up and I have to kill it thru system monitor.

Can someone please provide me with some direction?:confused:

---

