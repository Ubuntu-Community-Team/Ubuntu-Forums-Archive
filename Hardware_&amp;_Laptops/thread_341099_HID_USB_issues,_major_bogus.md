---
title: "HID USB issues, major bogus"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by jjabba on 2007-01-18
This is driving me crasy!!

I used Drapper on my system before and had no problems.
After "upgrading":-k to egy both my mouse and keyboard (both USB connected via KVM-switch) stopped working correctly.

The issue is constant usb-resetting causing the keys on my keyboard to either be non-responsive or repeat themselves.  "lllikkee tisss" (like this) ](*,) 

In my syslog i get this message over and over again:
```

Jan 18 12:53:44 jjabba-amd kernel: [17182862.012000] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
Jan 18 12:53:46 jjabba-amd kernel: [17182863.692000] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
Jan 18 12:53:47 jjabba-amd kernel: [17182865.348000] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
Jan 18 12:53:49 jjabba-amd kernel: [17182867.028000] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
Jan 18 12:53:51 jjabba-amd kernel: [17182868.676000] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
Jan 18 12:53:52 jjabba-amd kernel: [17182870.348000] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
```

I've read some posts about simular issues with USB-Harddrives etc, but this is effectively turning my ubuntu system unusable!

Here is my lshw, please please help my wth this 
```

jjabba-amd                
    description: Computer
    product: K7NF2-RAID
    version: 1.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: K7NF2-RAID
       physical id: 0
       version: 1.00
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30 (07/31/2006)
          size: 64KB
          capacity: 448KB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 6.8.1
          serial: To Be Filled By O.E.M.
          slot: CPU Socket
          size: 1800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 256KB
             capacity: 256KB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System memory
          physical id: 1
          size: 1011MB
     *-pci
          description: Host bridge
          product: nForce2 AGP (different version?)
          vendor: nVidia Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          resources: iomemory:f8000000-fbffffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-isa UNCLAIMED
             description: ISA bridge
             product: MCP2A ISA bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master cap_list
        *-serial
             description: SMBus
             product: MCP2A SMBus
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus
             resources: ioport:d480-d49f irq:10
        *-usb:0
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fc000-ff6fcfff irq:193
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb
                   description: USB hub
                   vendor: ATEN International Co., Ltd
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=200mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Keyboard
                      product: M2452
                      vendor: Alps Electric
                      physical id: 1
                      bus info: usb@2:1.1
                      version: 1.01
                      capabilities: usb-1.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
                 *-usb:1
                      description: Mouse
                      product: USB-PS/2 Optical Mouse
                      vendor: B16_b_02
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 98.02
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:ff6fb000-ff6fbfff irq:185
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ff6fdc00-ff6fdcff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 6
                   bus info: usb@3:6
                   version: 7.02
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
        *-bridge
             description: Ethernet interface
             product: MCP2A Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: a3
             serial: 00:13:8f:ce:35:9f
             size: 100000000
             capacity: 100000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=full ip=192.168.0.82 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:ff6fe000-ff6fefff ioport:dc00-dc07 irq:185
        *-multimedia
             description: Multimedia audio controller
             product: MCP2S AC'97 Audio Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:d800-d8ff ioport:e800-e87f iomemory:ff6ff000-ff6fffff irq:193
        *-pci:0
             description: PCI bridge
             product: MCP2A PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-multimedia:0
                description: Multimedia video controller
                product: Bt878 Video Capture
                vendor: Brooktree Corporation
                physical id: a
                bus info: pci@02:0a.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=bttv
                resources: iomemory:f6afe000-f6afefff irq:201
           *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: Bt878 Audio Capture
                vendor: Brooktree Corporation
                physical id: a.1
                bus info: pci@02:0a.1
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:f6aff000-f6afffff irq:201
        *-ide:0
             description: IDE interface
             product: MCP2A IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=AMD_IDE
             resources: ioport:ffa0-ffaf
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: ST3300831A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.03
                   serial: 3NF1506H
                   size: 279GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 279GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD reader
                   product: _NEC DV-5700B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.92
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-ide:1
             description: IDE interface
             product: nForce2 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@00:0b.0
             logical name: scsi0
             logical name: scsi1
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=sata_nv
             resources: ioport:ff8-fff ioport:ff0-ff3 ioport:fe8-fef ioport:fe0-fe3 ioport:e400-e40f ioport:e000-e07f irq:177
           *-disk
                description: SCSI Disk
                product: SAMSUNG HD401LJ
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ZZ10
                serial: S0HVJ1CLA13014
                size: 372GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 43GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 19GB
                   capabilities: primary
              *-volume:2
                   description: W95 Ext'd (LBA) partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 3067MB
                   capabilities: primary
              *-volume:3
                   description: HPFS/NTFS partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 306GB
                   capabilities: primary
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: R480 [Radeon X800 GTO (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e0000000-efffffff ioport:c800-c8ff iomemory:ff5f0000-ff5fffff irq:209
           *-display:1 UNCLAIMED
                description: Display controller
                product: R480 [Radeon X800 GTO (PCIE)] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 64KB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:ff5e0000-ff5effff

```

---

