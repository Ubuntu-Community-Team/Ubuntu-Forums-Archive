---
title: "udev failing to detect hard drives"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by rbarrimond on 2007-03-15
I have a Sonnet Trio card installed with 4 400GB UltraATA 133 drives connected to it.  Udev (or kernel?) detects the card no problem.  The excerpt from the lspci follows:
```
03:02.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02) (prog-if 85)
        Subsystem: Promise Technology, Inc. Unknown device ad69
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort+ <TAbort- <MAbort- >SERR- <PERR+
        Latency: 32 (1000ns min, 4500ns max), Cache Line Size: 16 bytes
        Interrupt: pin A routed to IRQ 6
        Region 0: I/O ports at cff0 [size=8]
        Region 1: I/O ports at cfe4 [size=4]
        Region 2: I/O ports at cfa8 [size=8]
        Region 3: I/O ports at cfe0 [size=4]
        Region 4: I/O ports at cf90 [size=16]
        Region 5: Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fe9e0000 [size=64K]
        Capabilities: [60] Power Management version 1
                Flags: PMEClk- DSI+ D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```...and dmesg output...```
[42949376.350000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[42949376.350000] ICH2: chipset revision 4
[42949376.350000] ICH2: not 100% native mode: will probe irqs later
[42949376.350000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[42949376.350000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[42949376.350000] Probing IDE interface ide0...
[42949377.250000] hda: CREATIVE CD5233E, ATAPI CD/DVD-ROM drive
[42949377.660000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949377.660000] Probing IDE interface ide1...
[42949378.010000] hdc: WDC WD200BB-00AUA1, ATA DISK drive
[42949378.850000] ide1 at 0x170-0x177,0x376 on irq 15
[42949378.890000] hdc: max request size: 128KiB
[42949378.890000] hdc: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[42949378.890000] hdc: cache flushes not supported
[42949378.890000]  hdc:<6>hda: ATAPI 56X CD-ROM drive, 128kB Cache, DMA
[42949378.890000] Uniform CD-ROM driver Revision: 3.20
[42949378.900000]  hdc1 hdc2 < hdc5 >
[42949379.210000] PDC20269: IDE controller at PCI slot 0000:03:02.0
[42949379.210000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 6
[42949379.210000] PCI: setting IRQ 6 as level-triggered
[42949379.210000] ACPI: PCI Interrupt 0000:03:02.0[A] -> Link [LNKB] -> GSI 6 (level, low) -> IRQ 6
[42949379.210000] PDC20269: chipset revision 2
[42949379.210000] PDC20269: ROM enabled at 0xfe9e0000
[42949379.210000] PDC20269: 100% native mode on irq 6
[42949379.210000]     ide2: BM-DMA at 0xcf90-0xcf97, BIOS settings: hde:DMA, hdf:DMA
[42949379.210000] PDC20269: simplex device: DMA disabled
[42949379.210000] ide3: PDC20269 Bus-Master DMA disabled (BIOS)
[42949379.210000] Probing IDE interface ide2...
[42949379.820000] Probing IDE interface ide3...
[42949380.620000] Probing IDE interface ide2...
[42949381.750000] Probing IDE interface ide3...
```But for the life of me I can't get udev to detect the drives connected to the card and create drive nodes.  I checked the cable connections, power, and jumpers.  All seem fine.  I only have the 20GB disk and the CD-ROM that are connected to the motherboard's controllers.  They work fine.  What am I missing?  Note: I'm totally clueless w.r.t. udev.

---

