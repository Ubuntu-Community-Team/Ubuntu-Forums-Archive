---
title: "Need help in setting up sound  under ubuntu 10.10"
date: 2011-03-13
forum: Hardware
---

### Post by mjsilverstri on 2011-03-13
I have installed ubuntu 10.10 on HP pavilion dv7 laptop.

It boots up but audio does not work.  

I did this

```
$ sudo aplay -l
[sudo] password for scheung: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And this

```
$ lspci -v 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: fast devsel
	Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d2000000-d30fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
	Subsystem: Device 003c:005c
	Flags: fast devsel
	Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
	Subsystem: Device 003c:005c
	Flags: fast devsel
	Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
	Subsystem: Device 003c:005c
	Flags: fast devsel
	Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
	Subsystem: Device 003c:005c
	Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
	Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
	Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at db105c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 53
	Memory at db100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: da100000-db0fffff
	Prefetchable memory behind bridge: 00000000d3100000-00000000d40fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d9100000-da0fffff
	Prefetchable memory behind bridge: 00000000d4100000-00000000d50fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d8100000-d90fffff
	Prefetchable memory behind bridge: 00000000d5100000-00000000d60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d7100000-d80fffff
	Prefetchable memory behind bridge: 00000000d6100000-00000000d70fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at db105800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 50
	I/O ports at 7048 [size=8]
	I/O ports at 7054 [size=4]
	I/O ports at 7040 [size=8]
	I/O ports at 7050 [size=4]
	I/O ports at 7020 [size=32]
	Memory at db105000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: medium devsel, IRQ 5
	Memory at db106000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 7000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 320M] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 6000 [size=128]
	[virtual] Expansion ROM at d3080000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at da100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 51
	I/O ports at 4000 [size=256]
	Memory at d4104000 (64-bit, prefetchable) [size=4K]
	Memory at d4100000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at d4110000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8100000 (32-bit, non-prefetchable) [size=2K]
	Memory at d8100d00 (32-bit, non-prefetchable) [size=128]
	Memory at d8100c80 (32-bit, non-prefetchable) [size=128]
	Memory at d8100c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8100b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: fast devsel, IRQ 16
	Memory at d8100a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8100900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d8100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0
	Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
	Subsystem: Hewlett-Packard Company Device 365c
	Flags: bus master, fast devsel, latency 0

```

Can you please tell me how to setup my sound for  ubuntu 10.10?

Thank you.

---

