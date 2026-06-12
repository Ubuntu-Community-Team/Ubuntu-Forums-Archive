---
title: "Is my SD supported?"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by ufa on 2006-07-27
Hi, 
My SD isnt giving life signals, so i want to know if it is working or not. here are some clues

lshw:

 *-storage UNCLAIMED
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@06:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                resources: iomemory:b0106000-b0107fff irq:11
           *-system
                description: Generic system peripheral
                product: PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
                vendor: Texas Instruments
                physical id: 9.4
                bus info: pci@06:09.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:b0109400-b01094ff iomemory:b0109000-b01090ff iomemory:b0108400-b01084ff irq:169




lspci:

0000:06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 11
        Memory at b0106000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2

0000:06:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 169
        Memory at b0109400 (32-bit, non-prefetchable) [size=256]
        Memory at b0109000 (32-bit, non-prefetchable) [size=256]
        Memory at b0108400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

But there is a strange thing in dmesg:

sdhci: ============== REGISTER DUMP ==============
[17179590.188000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179590.188000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179590.188000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179590.188000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179590.188000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179590.188000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179590.188000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179590.188000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179590.188000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179590.188000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179590.188000] sdhci: ===========================================
[17179590.240000] mmc0: SDHCI at 0xb0109400 irq 169 DMA
[17179590.340000] sdhci: ============== REGISTER DUMP ==============
[17179590.340000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179590.340000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179590.340000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179590.340000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179590.340000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179590.340000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179590.340000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179590.340000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179590.340000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179590.340000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179590.340000] sdhci: ===========================================
[17179590.388000] mmc1: SDHCI at 0xb0109000 irq 169 DMA
[17179590.488000] sdhci: ============== REGISTER DUMP ==============
[17179590.488000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179590.488000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179590.488000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179590.488000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179590.488000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179590.488000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179590.488000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179590.488000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179590.488000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179590.488000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179590.488000] sdhci: ===========================================
[17179590.536000] mmc2: SDHCI at 0xb0108400 irq 169 DMA


I tried to input a MMC and a SD card, but nothing changes in dmesg...does anyone have a clue?

Ufa

---

