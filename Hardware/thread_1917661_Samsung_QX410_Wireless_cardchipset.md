---
title: "Samsung QX410 Wireless card/chipset"
date: 2012-01-30
forum: Hardware
---

### Post by MikeVaughanG on 2012-01-30
I have a Samsung XQ410 Notebook. 


I'm trying to determine my what wireless card, and more importantly what chipset that wireless card uses. 

I found a tutorial that suggested I tried 2 commands, but I'm not sure what exactly I'm looking at, or if it's even there. 

Here's the output of those command. 

lspci-v
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e0000000-f30fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f3400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f600a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4c00000-f5ffffff
	Prefetchable memory behind bridge: 00000000f3100000-00000000f32fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f3800000-f4bfffff
	Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: medium devsel, IRQ 11
	Memory at f6005000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

01:00.0 3D controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at d000 [size=128]
	Expansion ROM at f3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)
	Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f4c00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
	Subsystem: Samsung Electronics Co Ltd Device c08b
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at f3820000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at b000 [size=256]
	Expansion ROM at f3800000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0
```

and 
lsusb
```
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1210:2604 DigiTech 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thanks in advance for all your help. :D
Mike Vaughan

---

### Post by Eirikke on 2012-03-22
Should be this entry...       02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)     Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN     Flags: bus master, fast devsel, latency 0, IRQ 44     Memory at f4c00000 (64-bit, non-prefetchable) [size=8K]     Capabilities:      Kernel driver in use: iwlagn     Kernel modules: iwlagn

---

