---
title: "Problem using USB 2.0"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by chicha on 2007-03-19
Hello all :) 

It seems I have 4 USB bus available on my machine :

```
chicha@Grogros:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

It seems USB Bus 4 is USB 2.0 compatible.

```
chicha@Grogros:~$ sudo lshw
grogros
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: i845PE-W83627
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (04/07/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: A1
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: d8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a4
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:dc000000-dcffffff iomemory:d0000000-d3ffffff irq:177
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e0000000-e00003ff irq:193
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Wireless interface
                product: ACX 111 54Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: c
                bus info: pci@02:0c.0
                logical name: wlan0
                version: 00
                serial: 00:0f:b5:8c:b2:3c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=acx_pci ip=192.168.0.1 multicast=yes wireless=IEEE 802.11b+/g+
                resources: iomemory:df020000-df021fff iomemory:df000000-df01ffff irq:177
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:f000-f00f iomemory:30000000-300003ff irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: HDS722580VLAT20
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: V32OA60A
                   serial: VNR21LC2SM4PNN
                   size: 76GB
                   capacity: 76GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10001MB
                      capabilities: primary bootable
                 *-volume:1
                      description: W95 Ext'd (LBA) partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 66GB
                      capabilities: primary
              *-disk:1
                   description: ATA Disk
                   product: WDC WD600BB-00CAA1
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 17.07W17
                   serial: WD-WMA8E2787130
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 55GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: _NEC DVD_RW ND-1300A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.06
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:500-51f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:e000-e0ff ioport:e400-e43f iomemory:e0001000-e00011ff iomemory:e0002000-e00020ff irq:201
```


Both USB 1.0 and 2.0 are activated :

```
chicha@Grogros:~$ lsmod | grep hci
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  7 snd_usb_audio,snd_usb_lib,gspca,acx,ehci_hcd,uhci_hcd
```

**Unfortunatly I cannot plug any USB device on USB Bus 4**.
I can see 3 UBS slots on my computer : 1 on the front (with 2 ports), 1 on the back (attached to the mother board, 2 ports) and 1 other on the back (PCI device, 2 ports).

I tried every USB port, and run lsusb after, and unfortunatly none of my USB port seem linked to USB Bus 4, the only one which interest me because it is USB 2.0 compatible :(

Do someone have any idea of what happen ?
Why is there a USB Bus 4, USB 2.0 compatible, if I cannot plug anything on it ?
Is there something to do on the mother board to plug my USB port on the right slot on the mother board ?

Thank you for you help !
Cheers,

Chicha

---

