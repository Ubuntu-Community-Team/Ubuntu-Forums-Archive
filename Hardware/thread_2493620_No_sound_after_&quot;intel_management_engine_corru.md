---
title: "No sound after &quot;intel management engine corrupted&quot;"
date: 2023-12-20
forum: Hardware
---

### Post by dvz3 on 2023-12-20
My HP 440 G7 was stuck in sleep state and I had to shut it off by holding power button for a minute.
On boot it said something about intel management engine corruption and proceeded to load Linux.
There was no sound and no internet solutions helped. So I loaded LiveISO and there was no sound either, and no sound after clean reinstall. I also tried Linux Mint 21.2 and there was no sound either.
There is still working sound in Windows 10 installation.

```
mz@dmz-HP440G7:~$ aplay --list-devices
aplay: device_list:277: no soundcards found...

```

```

dmz@dmz-HP440G7:~$ sudo lspci -v
[sudo] password for dmz: 
00:00.0 Host bridge: Intel Corporation Comet Lake-U v1 4c Host Bridge/DRAM Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Comet Lake-U v1 4c Host Bridge/DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel driver in use: skl_uncore

00:02.0 VGA compatible controller: Intel Corporation CometLake-U GT2 [UHD Graphics] (rev 02) (prog-if 00 [VGA controller])
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company CometLake-U GT2 [UHD Graphics]
    Flags: bus master, fast devsel, latency 0, IRQ 141
    Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)
    Kernel driver in use: i915
    Kernel modules: i915

00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0c)
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
    Flags: fast devsel, IRQ 16
    Memory at 4000100000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device_pci_legacy

00:12.0 Signal processing controller: Intel Corporation Comet Lake Thermal Subsytem
    Subsystem: Hewlett-Packard Company Comet Lake Thermal Subsytem
    Flags: fast devsel, IRQ 16
    Memory at 4000111000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal

00:14.0 USB controller: Intel Corporation Comet Lake PCH-LP USB 3.1 xHCI Host Controller (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company Comet Lake PCH-LP USB 3.1 xHCI Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 125
    Memory at f1300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

00:14.2 RAM memory: Intel Corporation Comet Lake PCH-LP Shared SRAM
    Subsystem: Hewlett-Packard Company Comet Lake PCH-LP Shared SRAM
    Flags: fast devsel
    Memory at f1312000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Memory at 4000110000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: [80] Power Management version 3

00:14.5 SD Host controller: Intel Corporation Comet Lake PCH-LP SCS3 (prog-if 01)
    Subsystem: Hewlett-Packard Company Comet Lake PCH-LP SCS3
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 400010f000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

00:15.0 Serial bus controller: Intel Corporation Serial IO I2C Host Controller
    Subsystem: Hewlett-Packard Company Serial IO I2C Host Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 400010e000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Comet Lake Management Engine Interface
    Subsystem: Hewlett-Packard Company Comet Lake Management Engine Interface
    Flags: bus master, fast devsel, latency 0, IRQ 138
    Memory at 400010d000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [a4] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Comet Lake SATA AHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 126
    Memory at f1310000 (32-bit, non-prefetchable) [size=8K]
    Memory at f1316000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5080 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5060 [size=32]
    Memory at f1315000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0) (prog-if 00 [Normal decode])
    Subsystem: Hewlett-Packard Company Comet Lake PCI Express Root Port
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 4000-4fff [size=4K] [16-bit]
    Memory behind bridge: f1200000-f12fffff [size=1M] [32-bit]
    Prefetchable memory behind bridge: [disabled] [64-bit]
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Comet Lake PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] Secondary PCI Express
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1d.1 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #10 (rev f0) (prog-if 00 [Normal decode])
    Subsystem: Hewlett-Packard Company Comet Lake PCI Express Root Port
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 3000-3fff [size=4K] [16-bit]
    Memory behind bridge: f1100000-f11fffff [size=1M] [32-bit]
    Prefetchable memory behind bridge: [disabled] [64-bit]
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Comet Lake PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [200] L1 PM Substates
    Capabilities: [220] Secondary PCI Express
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1d.4 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #13 (rev f0) (prog-if 00 [Normal decode])
    Subsystem: Hewlett-Packard Company Comet Lake PCI Express Root Port
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: [disabled] [16-bit]
    Memory behind bridge: f1000000-f10fffff [size=1M] [32-bit]
    Prefetchable memory behind bridge: [disabled] [64-bit]
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Comet Lake PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [200] L1 PM Substates
    Capabilities: [220] Secondary PCI Express
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1f.0 ISA bridge: Intel Corporation Comet Lake PCH-LP LPC Premium Controller/eSPI Controller
    Subsystem: Hewlett-Packard Company Comet Lake PCH-LP LPC Premium Controller/eSPI Controller
    Flags: bus master, fast devsel, latency 0

00:1f.3 Multimedia audio controller: Intel Corporation Comet Lake PCH-LP cAVS
    Subsystem: Hewlett-Packard Company Comet Lake PCH-LP cAVS
    Flags: bus master, fast devsel, latency 64, IRQ 16
    Memory at 4000108000 (64-bit, non-prefetchable) [size=16K]
    Memory at 4000000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: sof-audio-pci-intel-cnl
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_cnl

00:1f.4 SMBus: Intel Corporation Comet Lake PCH-LP SMBus Host Controller
    Subsystem: Hewlett-Packard Company Comet Lake PCH-LP SMBus Host Controller
    Flags: medium devsel, IRQ 16
    Memory at 400010c000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801

00:1f.5 Serial bus controller: Intel Corporation Comet Lake SPI (flash) Controller
    Subsystem: Hewlett-Packard Company Comet Lake SPI (flash) Controller
    Flags: fast devsel
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: intel-spi
    Kernel modules: spi_intel_pci

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 4000 [size=256]
    Memory at f1204000 (64-bit, non-prefetchable) [size=4K]
    Memory at f1200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable+ Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-e9-d3-3f-da-5c-b0
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822CE 802.11ac PCIe Wireless Network Adapter
    Subsystem: Hewlett-Packard Company RTL8822CE 802.11ac PCIe Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 140
    I/O ports at 3000 [size=256]
    Memory at f1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-e0-4c-ff-fe-c8-22-01
    Capabilities: [158] Latency Tolerance Reporting
    Capabilities: [160] L1 PM Substates
    Kernel driver in use: rtw_8822ce
    Kernel modules: rtw88_8822ce

03:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller 980 (prog-if 02 [NVM Express])
    Subsystem: Samsung Electronics Co Ltd NVMe SSD Controller 980
    Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 0
    Memory at f1000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [b0] MSI-X: Enable+ Count=13 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [158] Power Budgeting <?>
    Capabilities: [168] Secondary PCI Express
    Capabilities: [188] Latency Tolerance Reporting
    Capabilities: [190] L1 PM Substates
    Kernel driver in use: nvme
    Kernel modules: nvme



```

---

