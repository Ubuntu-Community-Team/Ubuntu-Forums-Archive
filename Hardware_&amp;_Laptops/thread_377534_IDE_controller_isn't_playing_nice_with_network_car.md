---
title: "IDE controller isn't playing nice with network card"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by pepolez on 2007-03-06
Today I installed a nice new IDE controller card in my PC, and now my network card doesn't seem to work. I'm not sure what to do here, as lshw lists the network card in question.

**IDE controller:** Silicon Image PCI0680 Ultra ATA-133 Host Controller
**Network card:** Realtek 8139 10/100 network card

**lshw:**
```

nibbler
    description: Desktop Computer
    product: KM400-8237
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-6734
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/28/2004)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd in
t13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14seria
l int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm)   2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1666MHz
          capacity: 2100MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca c
mov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: c0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:c0000000-cfffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600/GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a2
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                configuration: driver=nvidia
                resources: iomemory:e0000000-e0ffffff iomemory:d0000000-dfffffff iomemory:e1000000-
e1ffffff irq:217
        *-network:0 DISABLED
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@00:06.0
             logical name: eth2
             version: 10
             serial: ff:ff:ff:ff:ff:ff
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd
 autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 du
plex=full link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:9000-90ff iomemory:a4000000-a40000ff irq:201
        *-storage
             description: RAID bus controller
             product: PCI0680 Ultra ATA-133 Host Controller
             vendor: Silicon Image, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=SiI_IDE
             resources: ioport:9400-9407 ioport:9800-9803 ioport:9c00-9c07 ioport:a000-a003 ioport:
a400-a40f iomemory:e4001000-e40010ff irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: WDC WD800JB-00FMA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 13.03G13
                   serial: WD-WMAJ91083579
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10236MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 101MB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 509MB
                      capabilities: primary nofs
                 *-volume:3 UNCLAIMED
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      capacity: 63GB
                      capabilities: extended partitioned partitioned:extended
              *-disk:1
                   description: ATA Disk
                   product: ST3120022A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 8.54
                   serial: 5JS3GA1M
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume UNCLAIMED
                      description: W95 Ext'd (LBA) partition
                      physical id: 1
                      bus info: ide@0.1,1
                      capacity: 111GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1200BB-00DAA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 65.13G65
                   serial: WD-WMACK1255227
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 111GB
                      capabilities: primary
              *-cdrom
                   description: DVD reader
                   product: PIONEER DVD-117RD 0105
                   vendor: Pioneer
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.05
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dv
d
                   configuration: mode=udma4
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:a800-a80f irq:177
           *-ide
                description: IDE Channel 0
                physical id: 2
                bus info: ide@2
                logical name: ide2
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 0
                   bus info: ide@2.0
                   logical name: /dev/hde
                   version: A103
                   serial: K2653HC0948
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd
-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hde
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:ac00-ac1f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: USB hub
                   product: G11 Keyboard
                   vendor: Logitech, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.71
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Keyboard
                      product: Gaming Keyboard
                      vendor: Logitech, Inc.
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 1.90
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
                 *-usb:1
                      description: Human interface device
                      product: G11 Keyboard
                      vendor: Logitech, Inc.
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 1.71
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@1:2
                   version: 27.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b000-b01f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: ET-0405A-UV2.0-3
                   vendor: WACOM
                   physical id: 1
                   bus info: usb@2:1
                   version: 2.03
                   capabilities: usb-1.10
                   configuration: driver=wacom maxpower=40mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b800-b81f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e4002000-e40020ff irq:185
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: USB Mass Storage Device
                   vendor: Myson Century, Inc.
                   physical id: 6
                   bus info: usb@5:6
                   logical name: scsi0
                   version: b0.07
                   serial: 100
                   capabilities: usb-2.00 emulated scsi-host
                   configuration: driver=usb-storage maxpower=10mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: MHV2040AH
                      vendor: FUJITSU
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 0000
                      size: 37GB
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: W95 FAT32 partition
                         physical id: 1
                         bus info: scsi@0:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 37GB
                         capabilities: primary
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 7
                   bus info: usb@5:7
                   version: 6.0b
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:bc00-bcff irq:209
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
              *-usb:0
                   description: Mass storage device
                   product: USB Mass Storage Device
                   vendor: Myson Century, Inc.
                   physical id: 6
                   bus info: usb@5:6
                   logical name: scsi0
                   version: b0.07
                   serial: 100
                   capabilities: usb-2.00 emulated scsi-host
                   configuration: driver=usb-storage maxpower=10mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: MHV2040AH
                      vendor: FUJITSU
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 0000
                      size: 37GB
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: W95 FAT32 partition
                         physical id: 1
                         bus info: scsi@0:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 37GB
                         capabilities: primary
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 7
                   bus info: usb@5:7
                   version: 6.0b
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:bc00-bcff irq:209
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth1
             version: 78
             serial: 00:11:09:2c:59:e6
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=172.20.0.205 link=yes multicast=yes port=MII spe
ed=100MB/s
             resources: ioport:c000-c0ff iomemory:e4003000-e40030ff irq:193

```

**/etc/modules**
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse

```

Any help would be greatly appreciated :)

---

### Post by pepolez on 2007-03-06
Original post wouldn't let me add dmesg, so here's the dmesg output too

**dmesg**
```

[17179569.184000] Linux version 2.6.17-11-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Thu Feb 1 19:50:13 UTC 2007 (Ubuntu 2.6.17-11.35-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6560
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 KM400                                 ) @ 0x000f7f80
[17179569.184000] ACPI: RSDT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[17179569.184000] ACPI: FADT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[17179569.184000] ACPI: MADT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff7800
[17179569.184000] ACPI: DSDT (v001 KM400  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=f3b1da98-ae14-4044-b933-ac299f97b433 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1665.970 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.764000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.764000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.796000] Memory: 1028528k/1048512k available (1829k kernel code, 19276k reserved, 1041k data, 288k init, 131008k highmem)
[17179572.796000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.876000] Calibrating delay using timer specific routine.. 3335.34 BogoMIPS (lpj=6670687)
[17179572.876000] Security Framework v1.0.0 initialized
[17179572.876000] SELinux:  Disabled at boot.
[17179572.876000] Mount-cache hash table entries: 512
[17179572.876000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179572.876000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179572.876000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.876000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.876000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179572.876000] CPU: AMD Sempron(tm)   2400+ stepping 01
[17179572.876000] Checking 'hlt' instruction... OK.
[17179572.892000] SMP alternatives: switching to UP code
[17179572.892000] Freeing SMP alternatives: 0k freed
[17179572.892000] checking if image is initramfs... it is
[17179573.556000] Freeing initrd memory: 6714k freed
[17179573.556000] ACPI: Core revision 20060707
[17179573.564000] ACPI: Looking for DSDT ... not found!
[17179573.568000] ENABLING IO-APIC IRQs
[17179573.572000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.712000] NET: Registered protocol family 16
[17179573.712000] EISA bus registered
[17179573.712000] ACPI: bus type pci registered
[17179573.732000] PCI: PCI BIOS revision 2.10 entry at 0xfbcf0, last bus=1
[17179573.732000] PCI: Using configuration type 1
[17179573.732000] Setting up standard PCI resources
[17179573.756000] ACPI: Interpreter enabled
[17179573.756000] ACPI: Using IOAPIC for interrupt routing
[17179573.756000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.756000] PCI: Probing PCI hardware (bus 00)
[17179573.756000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.756000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[17179573.756000] PCI: Quirk-MSI-K8T Soundcard On
[17179573.756000] PCI: MSI-K8T soundcard on
[17179573.760000] Boot video device is 0000:01:00.0
[17179573.760000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.788000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[17179573.788000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[17179573.788000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[17179573.788000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179573.788000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179573.788000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179573.792000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179573.792000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179573.792000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *15, disabled.
[17179573.792000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[17179573.792000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[17179573.792000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[17179573.796000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.796000] pnp: PnP ACPI init
[17179573.800000] pnp: PnP ACPI: found 11 devices
[17179573.800000] PnPBIOS: Disabled by ACPI PNP
[17179573.800000] PCI: Using ACPI for IRQ routing
[17179573.800000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.824000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179573.824000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179573.824000] PCI: Bridge: 0000:00:01.0
[17179573.824000]   IO window: disabled.
[17179573.824000]   MEM window: e0000000-e2ffffff
[17179573.824000]   PREFETCH window: d0000000-dfffffff
[17179573.824000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.824000] NET: Registered protocol family 2
[17179573.864000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.864000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.864000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.864000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.864000] TCP reno registered
[17179573.864000] audit: initializing netlink socket (disabled)
[17179573.864000] audit(1173222339.864:1): initialized
[17179573.864000] highmem bounce pool size: 64 pages
[17179573.864000] VFS: Disk quotas dquot_6.5.1
[17179573.864000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.864000] Initializing Cryptographic API
[17179573.864000] io scheduler noop registered
[17179573.864000] io scheduler anticipatory registered
[17179573.864000] io scheduler deadline registered
[17179573.864000] io scheduler cfq registered (default)
[17179573.864000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179573.864000] isapnp: Scanning for PnP cards...
[17179574.220000] isapnp: No Plug & Play device found
[17179574.244000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.244000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.244000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.244000] mice: PS/2 mouse device common for all mice
[17179574.244000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.244000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.244000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.244000] PNP: No PS/2 controller found. Probing ports directly.
[17179574.244000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.244000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.248000] EISA: Probing bus 0 at eisa.0
[17179574.248000] Cannot allocate resource for EISA slot 4
[17179574.248000] Cannot allocate resource for EISA slot 5
[17179574.248000] EISA: Detected 0 cards.
[17179574.248000] TCP bic registered
[17179574.248000] NET: Registered protocol family 1
[17179574.248000] NET: Registered protocol family 8
[17179574.248000] NET: Registered protocol family 20
[17179574.248000] Using IPI Shortcut mode
[17179574.248000] ACPI: (supports S0 S1 S4 S5)
[17179574.248000] Freeing unused kernel memory: 288k freed
[17179575.388000] Capability LSM initialized
[17179575.424000] ACPI: Fan [FAN] (on)
[17179575.428000] ACPI: Thermal Zone [THRM] (48 C)
[17179575.948000] SiI680: IDE controller at PCI slot 0000:00:07.0
[17179575.948000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179575.948000] SiI680: chipset revision 2
[17179575.948000] SiI680: BASE CLOCK == 133
[17179575.948000] SiI680: 100% native mode on irq 169
[17179575.948000]     ide0: MMIO-DMA , BIOS settings: hda:pio, hdb:pio
[17179575.948000]     ide1: MMIO-DMA , BIOS settings: hdc:pio, hdd:pio
[17179575.948000] Probing IDE interface ide0...
[17179576.236000] hda: WDC WD800JB-00FMA0, ATA DISK drive
[17179576.516000] hdb: ST3120022A, ATA DISK drive
[17179576.572000] ide0 at 0xf8802080-0xf8802087,0xf880208a on irq 169
[17179576.572000] Probing IDE interface ide1...
[17179576.860000] hdc: WDC WD1200BB-00DAA0, ATA DISK drive
[17179577.308000] hdd: PIONEER DVD-117RD 0105, ATAPI CD/DVD-ROM drive
[17179577.364000] ide1 at 0xf88020c0-0xf88020c7,0xf88020ca on irq 169
[17179577.372000] hda: max request size: 64KiB
[17179577.388000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179577.388000] hda: cache flushes supported
[17179577.388000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 >
[17179577.444000] hdb: max request size: 64KiB
[17179577.444000] hdb: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.448000] hdb: cache flushes supported
[17179577.448000]  hdb: hdb1 < hdb5 >
[17179577.468000] hdc: max request size: 64KiB
[17179577.484000] hdc: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.484000] hdc: cache flushes supported
[17179577.484000]  hdc: hdc1
[17179577.520000] hdd: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(66)
[17179577.520000] Uniform CD-ROM driver Revision: 3.20
[17179578.184000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179578.184000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179578.184000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 15, using IRQ 20
[17179578.184000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179578.184000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 177
[17179578.184000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 1
[17179578.184000] VP_IDE: chipset revision 6
[17179578.184000] VP_IDE: not 100% native mode: will probe irqs later
[17179578.184000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179578.184000]     ide2: BM-DMA at 0xa800-0xa807, BIOS settings: hde:DMA, hdf:pio
[17179578.184000]     ide3: BM-DMA at 0xa808-0xa80f, BIOS settings: hdg:pio, hdh:pio
[17179578.184000] Probing IDE interface ide2...
[17179578.492000] hde: probing with STATUS(0x50) instead of ALTSTATUS(0x08)
[17179578.660000] hde: probing with STATUS(0x51) instead of ALTSTATUS(0x0a)
[17179578.940000] hde: probing with STATUS(0x51) instead of ALTSTATUS(0x0a)
[17179579.052000] hde: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
[17179579.388000] ide2 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179579.392000] hde: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.400000] Probing IDE interface ide3...
[17179580.056000] Probing IDE interface ide3...
[17179580.092000] usbcore: registered new driver usbfs
[17179580.092000] usbcore: registered new driver hub
[17179580.096000] USB Universal Host Controller Interface driver v3.0
[17179580.096000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179580.096000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179580.096000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 9
[17179580.096000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179580.096000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179580.096000] uhci_hcd 0000:00:10.0: irq 185, io base 0x0000ac00
[17179580.096000] usb usb1: configuration #1 chosen from 1 choice
[17179580.096000] hub 1-0:1.0: USB hub found
[17179580.096000] hub 1-0:1.0: 2 ports detected
[17179580.200000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179580.200000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 9
[17179580.200000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179580.200000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179580.200000] uhci_hcd 0000:00:10.1: irq 185, io base 0x0000b000
[17179580.200000] usb usb2: configuration #1 chosen from 1 choice
[17179580.200000] hub 2-0:1.0: USB hub found
[17179580.200000] hub 2-0:1.0: 2 ports detected
[17179580.304000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179580.304000] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 9
[17179580.304000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179580.304000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179580.304000] uhci_hcd 0000:00:10.2: irq 185, io base 0x0000b400
[17179580.304000] usb usb3: configuration #1 chosen from 1 choice
[17179580.304000] hub 3-0:1.0: USB hub found
[17179580.304000] hub 3-0:1.0: 2 ports detected
[17179580.408000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179580.408000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 9
[17179580.408000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179580.408000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179580.408000] uhci_hcd 0000:00:10.3: irq 185, io base 0x0000b800
[17179580.408000] usb usb4: configuration #1 chosen from 1 choice
[17179580.408000] hub 4-0:1.0: USB hub found
[17179580.408000] hub 4-0:1.0: 2 ports detected
[17179580.440000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179580.512000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
[17179580.512000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 9
[17179580.512000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179580.512000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179580.512000] ehci_hcd 0000:00:10.4: irq 185, io mem 0xe4002000
[17179580.512000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.516000] usb usb5: configuration #1 chosen from 1 choice
[17179580.516000] hub 5-0:1.0: USB hub found
[17179580.516000] hub 5-0:1.0: 8 ports detected
[17179580.964000] usb 1-1: device not accepting address 2, error -71
[17179581.344000] ReiserFS: hda5: found reiserfs format "3.6" with standard journal
[17179581.844000] ReiserFS: hda5: using ordered data mode
[17179581.852000] ReiserFS: hda5: journal params: device hda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179581.852000] ReiserFS: hda5: checking transaction log (hda5)
[17179581.884000] ReiserFS: hda5: Using r5 hash to sort names
[17179582.708000] usb 5-7: new high speed USB device using ehci_hcd and address 5
[17179582.840000] usb 5-7: configuration #1 chosen from 1 choice
[17179582.840000] hub 5-7:1.0: USB hub found
[17179582.840000] hub 5-7:1.0: 4 ports detected
[17179583.184000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17179583.348000] usb 1-1: configuration #1 chosen from 1 choice
[17179583.352000] hub 1-1:1.0: USB hub found
[17179583.356000] hub 1-1:1.0: 4 ports detected
[17179583.704000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[17179583.880000] usb 1-2: configuration #1 chosen from 1 choice
[17179584.120000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179584.292000] usb 2-1: configuration #1 chosen from 1 choice
[17179584.500000] usb 1-1.1: new low speed USB device using uhci_hcd and address 6
[17179584.632000] usb 1-1.1: configuration #1 chosen from 1 choice
[17179584.840000] usb 1-1.4: new full speed USB device using uhci_hcd and address 7
[17179584.976000] usb 1-1.4: configuration #1 chosen from 1 choice
[17179592.728000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.760000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179592.760000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179592.760000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 193
[17179592.760000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 1
[17179592.760000] eth0: VIA Rhine II at 0x1c000, 00:11:09:2c:59:e6, IRQ 193.
[17179592.764000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[17179592.804000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.804000] 8139cp: pci dev 0000:00:06.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179592.804000] 8139cp: Try the "8139too" driver instead.
[17179592.884000] 8139too Fast Ethernet driver 0.9.27
[17179592.884000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179592.884000] 8139too: 0000:00:06.0: unknown chip version, assuming RTL-8139
[17179592.884000] 8139too: 0000:00:06.0: TxConfig = 0xffffffff
[17179592.896000] eth1: RealTek RTL8139 at 0xf8898000, ff:ff:ff:ff:ff:ff, IRQ 201
[17179592.896000] eth1:  Identified 8139 chip type 'RTL-8139'
[17179593.164000] agpgart: Detected VIA KM400/KM400A chipset
[17179593.180000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179593.536000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.540000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.752000] Floppy drive(s): fd0 is 1.44M
[17179593.768000] FDC 0 is a post-1991 82077
[17179594.076000] Real Time Clock Driver v1.12ac
[17179594.088000] input: PC Speaker as /class/input/input0
[17179594.160000] parport: PnPBIOS parport detected.
[17179594.160000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179594.324000] usbcore: registered new driver hiddev
[17179594.348000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[17179594.348000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-2
[17179594.368000] input: Gaming Keyboard as /class/input/input2
[17179594.368000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:10.0-1.1
[17179594.404000] input: Gaming Keyboard as /class/input/input3
[17179594.404000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:10.0-1.1
[17179594.440000] input: G11 Keyboard as /class/input/input4
[17179594.440000] input,hiddev97: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:10.0-1.4
[17179594.440000] usbcore: registered new driver usbhid
[17179594.440000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179594.452000] input: Wacom Graphire2 4x5 as /class/input/input5
[17179594.556000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179594.556000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
[17179594.556000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 1
[17179594.556000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179594.804000] usbcore: registered new driver wacom
[17179594.804000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
[17179594.972000] nvidia: module license 'NVIDIA' taints kernel.
[17179595.048000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179595.100000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179595.104000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179595.496000] ts: Compaq touchscreen protocol output
[17179595.928000] lp0: using parport0 (interrupt-driven).
[17179595.996000] Unable to find swap-space signature
[17179596.136000] NET: Registered protocol family 17
[17179596.736000] NET: Registered protocol family 10
[17179596.736000] lo: Disabled Privacy Extensions
[17179596.736000] IPv6 over IPv4 tunneling driver
[17179601.820000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179601.820000] md: bitmap version 4.39
[17179601.976000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179606.808000] eth1: no IPv6 routers present
[17179651.924000] ReiserFS: hda6: found reiserfs format "3.6" with standard journal
[17179652.972000] ReiserFS: hda6: using ordered data mode
[17179652.984000] ReiserFS: hda6: journal params: device hda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179652.988000] ReiserFS: hda6: checking transaction log (hda6)
[17179653.012000] ReiserFS: hda6: Using r5 hash to sort names
[17179653.232000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179653.292000] NTFS volume version 3.1.
[17179653.324000] Unable to find swap-space signature
[17179654.932000] pcc_acpi: loading...
[17179654.948000] ACPI: Power Button (FF) [PWRF]
[17179654.948000] ACPI: Power Button (CM) [PWRB]
[17179654.948000] ACPI: Sleep Button (CM) [SLPB]
[17179655.000000] ibm_acpi: ec object not found
[17179655.332000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179656.972000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179656.972000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179656.972000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179658.020000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179658.020000] apm: overridden by ACPI.
[17179668.052000] usb 5-6: new high speed USB device using ehci_hcd and address 6
[17179668.188000] usb 5-6: configuration #1 chosen from 1 choice
[17179668.304000] usbcore: registered new driver libusual
[17179668.392000] SCSI subsystem initialized
[17179668.396000] Initializing USB Mass Storage driver...
[17179668.396000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179668.396000] usb-storage: device found at 6
[17179668.396000] usb-storage: waiting for device to settle before scanning
[17179668.396000] usbcore: registered new driver usb-storage
[17179668.396000] USB Mass Storage support registered.
[17179669.956000] Bluetooth: Core ver 2.8
[17179669.956000] NET: Registered protocol family 31
[17179669.956000] Bluetooth: HCI device and connection manager initialized
[17179669.956000] Bluetooth: HCI socket layer initialized
[17179669.984000] Bluetooth: L2CAP ver 2.8
[17179669.984000] Bluetooth: L2CAP socket layer initialized
[17179670.032000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179670.096000] Bluetooth: RFCOMM socket layer initialized
[17179670.096000] Bluetooth: RFCOMM TTY layer initialized
[17179670.096000] Bluetooth: RFCOMM ver 1.7
[17179673.396000] usb-storage: device scan complete
[17179673.396000]   Vendor: FUJITSU   Model: MHV2040AH         Rev: 0000
[17179673.396000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179673.448000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17179673.448000] sda: Write Protect is off
[17179673.448000] sda: Mode Sense: 00 14 00 00
[17179673.448000] sda: assuming drive cache: write through
[17179673.452000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17179673.452000] sda: Write Protect is off
[17179673.452000] sda: Mode Sense: 00 14 00 00
[17179673.452000] sda: assuming drive cache: write through
[17179673.452000]  sda: sda1
[17179673.480000] sd 0:0:0:0: Attached scsi disk sda
[17179673.528000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179687.276000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179962.100000] ReiserFS: hdc1: warning: unknown mount option "utf8"
[17179991.712000] ReiserFS: hdc1: found reiserfs format "3.6" with standard journal
[17179997.840000] ReiserFS: hdc1: using ordered data mode
[17179997.856000] ReiserFS: hdc1: journal params: device hdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179997.860000] ReiserFS: hdc1: checking transaction log (hdc1)
[17179997.936000] ReiserFS: hdc1: Using r5 hash to sort names
[17180648.308000] hdd: tray open
[17180648.308000] end_request: I/O error, dev hdd, sector 0
[17180648.308000] Buffer I/O error on device hdd, logical block 0
[17180648.308000] hdd: tray open
[17180648.308000] end_request: I/O error, dev hdd, sector 4
[17180648.308000] Buffer I/O error on device hdd, logical block 1
[17180648.312000] hdd: tray open
[17180648.312000] end_request: I/O error, dev hdd, sector 8
[17180648.312000] Buffer I/O error on device hdd, logical block 2
[17180648.312000] hdd: tray open
[17180648.312000] end_request: I/O error, dev hdd, sector 12
[17180648.312000] Buffer I/O error on device hdd, logical block 3
[17180648.312000] hdd: tray open
[17180648.312000] end_request: I/O error, dev hdd, sector 16
[17180648.312000] Buffer I/O error on device hdd, logical block 4
[17180648.312000] hdd: tray open
[17180648.312000] end_request: I/O error, dev hdd, sector 20
[17180648.312000] Buffer I/O error on device hdd, logical block 5
[17180648.312000] hdd: tray open
[17180648.312000] end_request: I/O error, dev hdd, sector 24
[17180648.312000] Buffer I/O error on device hdd, logical block 6
[17180648.312000] hdd: tray open
[17180648.312000] end_request: I/O error, dev hdd, sector 28
[17180648.312000] Buffer I/O error on device hdd, logical block 7
[17180648.316000] hdd: tray open
[17180648.316000] end_request: I/O error, dev hdd, sector 0
[17180648.316000] Buffer I/O error on device hdd, logical block 0
[17180648.316000] hdd: tray open
[17180648.316000] end_request: I/O error, dev hdd, sector 4
[17180648.316000] Buffer I/O error on device hdd, logical block 1
[17180648.316000] hdd: tray open
[17180648.316000] end_request: I/O error, dev hdd, sector 0
[17180648.316000] hdd: tray open
[17180648.316000] end_request: I/O error, dev hdd, sector 4
[17180648.316000] hdd: tray open
[17180648.316000] end_request: I/O error, dev hdd, sector 0
[17180648.316000] hdd: tray open
[17180648.316000] end_request: I/O error, dev hdd, sector 4
[17180648.376000] hde: tray open
[17180648.376000] end_request: I/O error, dev hde, sector 0
[17180648.376000] hde: tray open
[17180648.376000] end_request: I/O error, dev hde, sector 4
[17180648.380000] hde: tray open
[17180648.380000] end_request: I/O error, dev hde, sector 8
[17180648.380000] hde: tray open
[17180648.380000] end_request: I/O error, dev hde, sector 12
[17180648.384000] hde: tray open
[17180648.384000] end_request: I/O error, dev hde, sector 16
[17180648.384000] hde: tray open
[17180648.384000] end_request: I/O error, dev hde, sector 20
[17180648.388000] hde: tray open
[17180648.388000] end_request: I/O error, dev hde, sector 24
[17180648.388000] hde: tray open
[17180648.388000] end_request: I/O error, dev hde, sector 28
[17180648.392000] hde: tray open
[17180648.392000] end_request: I/O error, dev hde, sector 0
[17180648.392000] hde: tray open
[17180648.392000] end_request: I/O error, dev hde, sector 4
[17180648.396000] hde: tray open
[17180648.396000] end_request: I/O error, dev hde, sector 0
[17180648.396000] hde: tray open
[17180648.396000] end_request: I/O error, dev hde, sector 4
[17180648.400000] hde: tray open
[17180648.400000] end_request: I/O error, dev hde, sector 0
[17180648.404000] hde: tray open
[17180648.404000] end_request: I/O error, dev hde, sector 4
[17180671.660000] hdd: tray open
[17180671.660000] end_request: I/O error, dev hdd, sector 0
[17180671.660000] printk: 18 messages suppressed.
[17180671.660000] Buffer I/O error on device hdd, logical block 0
[17180671.660000] hdd: tray open
[17180671.660000] end_request: I/O error, dev hdd, sector 4
[17180671.660000] Buffer I/O error on device hdd, logical block 1
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 8
[17180671.664000] Buffer I/O error on device hdd, logical block 2
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 12
[17180671.664000] Buffer I/O error on device hdd, logical block 3
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 16
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 20
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 24
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 28
[17180671.664000] hdd: tray open
[17180671.664000] end_request: I/O error, dev hdd, sector 0
[17180671.668000] hdd: tray open
[17180671.668000] end_request: I/O error, dev hdd, sector 4
[17180671.668000] hdd: tray open
[17180671.668000] end_request: I/O error, dev hdd, sector 0
[17180671.668000] hdd: tray open
[17180671.668000] end_request: I/O error, dev hdd, sector 4
[17180671.668000] hdd: tray open
[17180671.668000] end_request: I/O error, dev hdd, sector 0
[17180671.668000] hdd: tray open
[17180671.668000] end_request: I/O error, dev hdd, sector 4
[17180671.728000] hde: tray open
[17180671.728000] end_request: I/O error, dev hde, sector 0
[17180671.728000] hde: tray open
[17180671.728000] end_request: I/O error, dev hde, sector 4
[17180671.732000] hde: tray open
[17180671.732000] end_request: I/O error, dev hde, sector 8
[17180671.732000] hde: tray open
[17180671.732000] end_request: I/O error, dev hde, sector 12
[17180671.736000] hde: tray open
[17180671.736000] end_request: I/O error, dev hde, sector 16
[17180671.736000] hde: tray open
[17180671.736000] end_request: I/O error, dev hde, sector 20
[17180671.740000] hde: tray open
[17180671.740000] end_request: I/O error, dev hde, sector 24
[17180671.740000] hde: tray open
[17180671.740000] end_request: I/O error, dev hde, sector 28
[17180671.744000] hde: tray open
[17180671.744000] end_request: I/O error, dev hde, sector 0
[17180671.744000] hde: tray open
[17180671.744000] end_request: I/O error, dev hde, sector 4
[17180671.748000] hde: tray open
[17180671.748000] end_request: I/O error, dev hde, sector 0
[17180671.748000] hde: tray open
[17180671.748000] end_request: I/O error, dev hde, sector 4
[17180671.752000] hde: tray open
[17180671.752000] end_request: I/O error, dev hde, sector 0
[17180671.756000] hde: tray open
[17180671.756000] end_request: I/O error, dev hde, sector 4
[17180687.516000] hdd: tray open
[17180687.516000] end_request: I/O error, dev hdd, sector 0
[17180687.516000] printk: 24 messages suppressed.
[17180687.516000] Buffer I/O error on device hdd, logical block 0
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 4
[17180687.520000] Buffer I/O error on device hdd, logical block 1
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 8
[17180687.520000] Buffer I/O error on device hdd, logical block 2
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 12
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 16
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 20
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 24
[17180687.520000] hdd: tray open
[17180687.520000] end_request: I/O error, dev hdd, sector 28
[17180687.524000] hdd: tray open
[17180687.524000] end_request: I/O error, dev hdd, sector 0
[17180687.524000] hdd: tray open
[17180687.524000] end_request: I/O error, dev hdd, sector 4
[17180687.524000] hdd: tray open
[17180687.524000] end_request: I/O error, dev hdd, sector 0
[17180687.524000] hdd: tray open
[17180687.524000] end_request: I/O error, dev hdd, sector 4
[17180687.524000] hdd: tray open
[17180687.524000] end_request: I/O error, dev hdd, sector 0
[17180687.524000] hdd: tray open
[17180687.524000] end_request: I/O error, dev hdd, sector 4
[17180687.580000] hde: tray open
[17180687.580000] end_request: I/O error, dev hde, sector 0
[17180687.580000] hde: tray open
[17180687.580000] end_request: I/O error, dev hde, sector 4
[17180687.584000] hde: tray open
[17180687.584000] end_request: I/O error, dev hde, sector 8
[17180687.588000] hde: tray open
[17180687.588000] end_request: I/O error, dev hde, sector 12
[17180687.588000] hde: tray open
[17180687.588000] end_request: I/O error, dev hde, sector 16
[17180687.592000] hde: tray open
[17180687.592000] end_request: I/O error, dev hde, sector 20
[17180687.592000] hde: tray open
[17180687.592000] end_request: I/O error, dev hde, sector 24
[17180687.596000] hde: tray open
[17180687.596000] end_request: I/O error, dev hde, sector 28
[17180687.596000] hde: tray open
[17180687.596000] end_request: I/O error, dev hde, sector 0
[17180687.600000] hde: tray open
[17180687.600000] end_request: I/O error, dev hde, sector 4
[17180687.600000] hde: tray open
[17180687.600000] end_request: I/O error, dev hde, sector 0
[17180687.604000] hde: tray open
[17180687.604000] end_request: I/O error, dev hde, sector 4
[17180687.604000] hde: tray open
[17180687.604000] end_request: I/O error, dev hde, sector 0
[17180687.608000] hde: tray open
[17180687.608000] end_request: I/O error, dev hde, sector 4

```

---

### Post by pepolez on 2007-03-07
Nevermind, I got it working after a while by rearranging the order of the PCI cards :D

---

### Post by bravemosquito on 2007-03-08
> **pepolez said:**
> Nevermind, I got it working after a while by rearranging the order of the PCI cards :D

This is an old bug of IRQ conflicts. I had exactly same problem on different pcs and oses. Main reason for that problem is badly configured BIOS, second and also frequently happened is OS's bad support/handling of external cards

---

