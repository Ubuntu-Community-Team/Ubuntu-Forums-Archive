---
title: "Parallel Port"
date: 2015-01-26
forum: Hardware
---

### Post by hamid2 on 2015-01-26
Hi 
  I recently downloaded ubuntu 14 for a project and started using it so I dont know much about it. I want to sync it with an EEG device using parallel port, the programs Im using are Matlab and Psychopy (a Python base program) but unfortunatly there was no success.
  Here is ```
lspci -v  
``` command,as it has been shown there is a serial controller but no parallel controller, and there is no /dev/parport0 or /dev/lp0 on my computer. 
  What is the problem? Is the device unknown for ubuntu? What should I do??   :(:(:mad:


```
erp@erp-System-Product-Name:~$ sudo lspci -v
[sudo] password for erp: 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f7100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f711b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7118000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7110000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f21fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7117000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 84ca

00:1f.0 ISA bridge: Intel Corporation B75 Express Chipset LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7116000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: medium devsel, IRQ 14
    Memory at f7115000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8460
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nouveau

01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8460
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at d000 [size=256]
    Memory at f2104000 (64-bit, prefetchable) [size=4K]
    Memory at f2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 22-02-00-00-68-4c-e0-00
    Kernel driver in use: r8169

04:00.0 Serial controller: Device 4348:5053 (rev 10) (prog-if 02 [16550])
    Subsystem: Device 4348:5053
    Flags: medium devsel, IRQ 16
    I/O ports at c010 [size=8]
    I/O ports at c000 [size=8]
    Kernel driver in use: serial
```

Please help me .
Thanks

---

### Post by Handssolow on 2015-01-26
Does you motherboard have a parallel port? Mine doesn't but I have a printer with a parallel interface.

I'd been using with very mixed success a USB to parallel adaptor cable for Brother Laser printer, sometimes it would work sometimes not. A replacement cable was no different. A couple of days ago I added a PCI parallel card to the desktop PC and all is working. Here is the relevant lspci -v output-

04:06.2 Parallel controller: MosChip Semiconductor Technology Ltd. PCI 9865 Multi-I/O Controller (prog-if 03 [IEEE1284])
	Subsystem: Device a000:2000
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at c090 [size=8]
	I/O ports at c080 [size=8]
	Memory at fe302000 (32-bit, non-prefetchable) [size=4K]
	Memory at fe301000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [48] Power Management version 2
	Kernel driver in use: parport_pc
	Kernel modules: parport_pc

---

### Post by hamid2 on 2015-01-27
Thanks for your reply

 because the motherboard doesn't have an onboard parallel port I used a PCI parallel card with WCH352L chipset but as you saw it's not in the lspci list

---

### Post by Handssolow on 2015-01-27
MosChip Semiconductor Technology Ltd seem to be the manfacturer of the chip in both our parallel port cards though I'm not sure if they are the same. I've looked on my blue and white box and it just says "Professional Manufacture for Computer Hardware Components". The instructions for mine says its from NetMos Technology.

Generally I've had problems in the past with some wifi cards which weren't recognised by Ubuntu. Recently I bought a USB 3 card to feed the front panel's USB slots as there was no USB 3 header on the mobo. I used the reviews in Amazon to find someone reporting that things works under Linux. It wasn't a StarTech USB 3 card, too many people reported problems.

Have you got access to another OS to see if the card is recognised and working, a live CD perhaps?

As mentioned earlier I didn't have a lot of success with the Parallel to USB adaptor cables.

---

### Post by hamid2 on 2015-01-27
I tried it with windows 7 and it had problems with the driver there too but finilly worked properly,so the card is ok. Maybe ubuntu doesn't support this card and I have to buy another card like yours.

---

