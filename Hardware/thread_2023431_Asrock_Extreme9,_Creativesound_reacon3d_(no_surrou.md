---
title: "Asrock Extreme9, Creativesound reacon3d (no surround)"
date: 2012-07-12
forum: Hardware
---

### Post by Rukiri on 2012-07-12
For the past few hours I've been trying to get my surround  speakers working, well I COULD just use Nvidia's HDMI input and go  through a AV Reciever but I'm not using an AV reciever but just some  Logitech 5.1 speakers(Green, pink, black) ya know 5.1
I have read  both pulse-audio and alsa and tried everything that was in the wiki but  that didn't solve the issue, so when all else fails aks the community.
Now, my sound card came with my motherboard as a PCI card.
You can find more info on that here.
[http://www.asrock.com/mb/overview.asp?M … 20Extreme9]("http://www.asrock.com/mb/overview.asp?Model=X79%20Extreme9")
Obviously all windows drivers so.. no help there.
I'm just wondering if anyone has the same card and figured out this issue?
Thanks!

---

### Post by jmfal on 2012-07-12
Welcome to Ubuntu

Run this in a terminal, this will list all sound cards
```
 aplay -l   
```
and
```
 lspci -v   
```

Please copy/paste the output between the [code][code] brackets using #

---

### Post by Rukiri on 2012-07-12
```

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=10, subordinate=10, sec-latency=32
    Capabilities: [50] Subsystem: ASRock Incorporation Device 244e

00:1f.0 ISA bridge: Intel Corporation C600/X79 series chipset LPC Controller (rev 05)
    Subsystem: ASRock Incorporation Device 1d41
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:1f.2 SATA controller: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 1d02
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 85
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at f4b25000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation C600/X79 series chipset SMBus Host Controller (rev 05)
    Subsystem: ASRock Incorporation Device 1d22
    Flags: medium devsel, IRQ 18
    Memory at f4b24000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel driver in use: i801_smbus

02:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 680] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 0969
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at d8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f4000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia

02:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation Device 0969
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at f4080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)
    Subsystem: ASRock Incorporation Device 96b1
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at da210000 (64-bit, prefetchable) [size=64K]
    Memory at da200000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at f4a00000 [disabled] [size=2K]
    Capabilities: [48] Power Management version 3
    Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [a0] MSI-X: Enable+ Count=5 Masked-
    Capabilities: [ac] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Device Serial Number 00-00-bc-5f-f4-1e-83-f2
    Capabilities: [150] Power Budgeting <?>
    Capabilities: [160] Virtual Channel
    Kernel driver in use: tg3

06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 9172
    Flags: bus master, fast devsel, latency 0, IRQ 86
    I/O ports at d040 [size=8]
    I/O ports at d030 [size=4]
    I/O ports at d020 [size=8]
    I/O ports at d010 [size=4]
    I/O ports at d000 [size=16]
    Memory at f4910000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at f4900000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: ahci

07:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 9172
    Flags: bus master, fast devsel, latency 0, IRQ 87
    I/O ports at c040 [size=8]
    I/O ports at c030 [size=4]
    I/O ports at c020 [size=8]
    I/O ports at c010 [size=4]
    I/O ports at c000 [size=16]
    Memory at f4810000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at f4800000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: ahci

08:00.0 PCI bridge: PLX Technology, Inc. Device 8605 (rev aa) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Memory at f4400000 (32-bit, non-prefetchable) [size=16K]
    Bus: primary=08, secondary=09, subordinate=0c, sec-latency=0
    I/O behind bridge: 00009000-0000afff
    Memory behind bridge: f4100000-f43fffff
    Prefetchable memory behind bridge: 00000000da100000-00000000da1fffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/4 Maskable+ 64bit+
    Capabilities: [68] Express Upstream Port, MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8605
    Capabilities: [100] Device Serial Number aa-86-02-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [138] Power Budgeting <?>
    Capabilities: [148] Virtual Channel
    Capabilities: [950] Vendor Specific Information: ID=0001 Rev=0 Len=028 <?>
    Kernel driver in use: pcieport

09:01.0 PCI bridge: PLX Technology, Inc. Device 8605 (rev aa) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=09, secondary=0a, subordinate=0a, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f4300000-f43fffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/4 Maskable+ 64bit+
    Capabilities: [68] Express Downstream Port (Slot+), MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8605
    Capabilities: [100] Device Serial Number aa-86-02-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [148] Virtual Channel
    Capabilities: [520] Access Control Services
    Capabilities: [950] Vendor Specific Information: ID=0001 Rev=0 Len=028 <?>
    Kernel driver in use: pcieport

09:02.0 PCI bridge: PLX Technology, Inc. Device 8605 (rev aa) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=09, secondary=0b, subordinate=0b, sec-latency=0
    Memory behind bridge: f4200000-f42fffff
    Prefetchable memory behind bridge: 00000000da100000-00000000da1fffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/4 Maskable+ 64bit+
    Capabilities: [68] Express Downstream Port (Slot+), MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8605
    Capabilities: [100] Device Serial Number aa-86-02-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [148] Virtual Channel
    Capabilities: [520] Access Control Services
    Capabilities: [950] Vendor Specific Information: ID=0001 Rev=0 Len=028 <?>
    Kernel driver in use: pcieport

09:03.0 PCI bridge: PLX Technology, Inc. Device 8605 (rev aa) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=09, secondary=0c, subordinate=0c, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: f4100000-f41fffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/4 Maskable+ 64bit+
    Capabilities: [68] Express Downstream Port (Slot+), MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8605
    Capabilities: [100] Device Serial Number aa-86-02-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [148] Virtual Channel
    Capabilities: [520] Access Control Services
    Capabilities: [950] Vendor Specific Information: ID=0001 Rev=0 Len=028 <?>
    Kernel driver in use: pcieport

0a:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01) (prog-if 10 [OHCI])
    Subsystem: ASRock Incorporation Device 3403
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4300000 (64-bit, non-prefetchable) [size=2K]
    I/O ports at a000 [size=256]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [98] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [130] Device Serial Number 25-ff-ff-13-8f-00-00-00
    Kernel driver in use: firewire_ohci

0b:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)
    Subsystem: ASRock Incorporation Device 96b1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at da110000 (64-bit, prefetchable) [size=64K]
    Memory at da100000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at f4200000 [disabled] [size=2K]
    Capabilities: [48] Power Management version 3
    Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [a0] MSI-X: Enable- Count=5 Masked-
    Capabilities: [ac] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Device Serial Number 00-00-bc-5f-f4-20-13-3a
    Capabilities: [150] Power Budgeting <?>
    Capabilities: [160] Virtual Channel
    Kernel driver in use: tg3

0c:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 9172
    Flags: bus master, fast devsel, latency 0, IRQ 88
    I/O ports at 9040 [size=8]
    I/O ports at 9030 [size=4]
    I/O ports at 9020 [size=8]
    I/O ports at 9010 [size=4]
    I/O ports at 9000 [size=16]
    Memory at f4110000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at f4100000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: ahci

0d:00.0 SATA controller: Marvell Technology Group Ltd. Device 9220 (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 9220
    Flags: bus master, fast devsel, latency 0, IRQ 89
    I/O ports at b050 [size=8]
    I/O ports at b040 [size=4]
    I/O ports at b030 [size=8]
    I/O ports at b020 [size=4]
    I/O ports at b000 [size=32]
    Memory at f4710000 (32-bit, non-prefetchable) [size=2K]
    Expansion ROM at f4700000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [e0] SATA HBA v0.0
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: ahci

0e:00.0 USB controller: Texas Instruments Device 8241 (rev 02) (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device 8241
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f4600000 (64-bit, non-prefetchable) [size=64K]
    Memory at f4610000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [c0] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Device Serial Number 08-00-28-00-00-20-00-00
    Kernel driver in use: xhci_hcd

0f:00.0 USB controller: Texas Instruments Device 8241 (rev 02) (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device 8241
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4500000 (64-bit, non-prefetchable) [size=64K]
    Memory at f4510000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [c0] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Device Serial Number 08-00-28-00-00-20-00-00
    Kernel driver in use: xhci_hcd

ff:08.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3c80
    Flags: fast devsel

ff:08.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3c83
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=0 Len=0f0 <?>

ff:08.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3c84
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:09.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3c90
    Flags: fast devsel

ff:09.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3c93
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=0 Len=0f0 <?>

ff:09.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3c94
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0a.0 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3cc0
    Flags: fast devsel

ff:0a.1 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3cc1
    Flags: fast devsel

ff:0a.2 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 (rev 07)
    Subsystem: ASRock Incorporation Device 3cc2
    Flags: fast devsel

ff:0a.3 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 (rev 07)
    Subsystem: ASRock Incorporation Device 3cd0
    Flags: fast devsel

ff:0b.0 System peripheral: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers (rev 07)
    Subsystem: ASRock Incorporation Device 3ce0
    Flags: fast devsel

ff:0b.3 System peripheral: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers (rev 07)
    Subsystem: ASRock Incorporation Device 3ce3
    Flags: fast devsel

ff:0c.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0c.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0c.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0c.7 System peripheral: Intel Corporation Xeon E5/Core i7 System Address Decoder (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0d.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0d.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0d.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3ce8
    Flags: fast devsel

ff:0e.0 System peripheral: Intel Corporation Xeon E5/Core i7 Processor Home Agent (rev 07)
    Subsystem: ASRock Incorporation Device 3ca0
    Flags: fast devsel

ff:0e.1 Performance counters: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring (rev 07)
    Subsystem: ASRock Incorporation Device 3c46
    Flags: fast devsel

ff:0f.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers (rev 07)
    Subsystem: ASRock Incorporation Device 3ca8
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers (rev 07)
    Subsystem: ASRock Incorporation Device 3c71
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3caa
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3cab
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 (rev 07)
    Subsystem: ASRock Incorporation Device 3cac
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 (rev 07)
    Subsystem: ASRock Incorporation Device 3cad
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 (rev 07)
    Subsystem: ASRock Incorporation Device 3cae
    Flags: fast devsel

ff:10.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb0
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb1
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb2
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb3
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb4
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb5
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb6
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.7 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 (rev 07)
    Subsystem: ASRock Incorporation Device 3cb7
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:11.0 System peripheral: Intel Corporation Xeon E5/Core i7 DDRIO (rev 07)
    Subsystem: ASRock Incorporation Device 3cb8
    Flags: fast devsel

ff:13.0 System peripheral: Intel Corporation Xeon E5/Core i7 R2PCIe (rev 07)
    Subsystem: ASRock Incorporation Device 3ce4
    Flags: fast devsel

ff:13.1 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor (rev 07)
    Subsystem: ASRock Incorporation Device 3c43
    Flags: fast devsel

ff:13.4 Performance counters: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers (rev 07)
    Subsystem: ASRock Incorporation Device 3ce6
    Flags: fast devsel

ff:13.5 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor (rev 07)
    Subsystem: ASRock Incorporation Device 3c44
    Flags: fast devsel

ff:13.6 System peripheral: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor (rev 07)
    Subsystem: ASRock Incorporation Device 3c45
    Flags: fast devsel 

```

---

### Post by jmfal on 2012-07-12
Can you post   "aplay -l"

---

### Post by Rukiri on 2012-07-12
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by jmfal on 2012-07-12
Try this
```
  sudo mosprobe snd-ca0132   
```

Make sure all speaker controls are unmuted and turned up in alsamixer and play some music

---

### Post by Rukiri on 2012-07-12
```

FATAL: Module snd-ca0132 not found.

```

---

### Post by jmfal on 2012-07-12
I'm going to suggest you try this how-to , just copy/ paste the commands into a terminal

Your sound kernal is not being reecognized so this will pull in  that resource, it looks intimidating but its not ,, just follow instructions carefully, any problems just post back here

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Make sure you enter commands for your version (12.04,11.10,etc...) if specified..

---

