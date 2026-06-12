---
title: "USB stops working after some time"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by yu_raider on 2006-12-25
Hi,

I have a problem with my Ubuntu Dapper, ANY device that I connect via USB works for a few seconds, then just stops. I tried connecting a USB mouse, USB modem, my MP3 player, but regardless of the device I always experience the same problem.

Any idea on how to fix this?

Thanks in advance :).

---

### Post by xyz on 2006-12-25
Hi,
Try and tell us a bit more about your computer! Brand, etc!
You could go Application > Accessories > Terminal - copy/paste + Enter this there:
```
lshw
```
'ls' = list  'hw' = hard ware

---

### Post by yu_raider on 2006-12-25
Thanks for the quick reply. Here's the output:

```

    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: nVidia-nForce
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (05/25/1905)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2200MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GB
          capacity: 1536MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
     *-pci
          description: Host bridge
          product: nForce2 AGP (different version?)
          vendor: nVidia Corporation
          physical id: c0000000
          bus info: pci@00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          resources: iomemory:c0000000-dfffffff
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
             resources: ioport:e500-e51f irq:9
        *-usb:0
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
             resources: iomemory:ec003000-ec003fff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Creative WebCam Vista Plus.
                   vendor: Creative
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:1
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
             resources: iomemory:ec004000-ec004fff irq:11
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
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
             resources: iomemory:ec005000-ec0050ff irq:9
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-23-386 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-bridge
             description: Ethernet interface
             product: MCP2A Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: a3
             serial: 00:04:61:75:b3:0e
             size: 100000000
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.48 duplex=full ip=192.168.0.1 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:ec000000-ec000fff ioport:e000-e007 irq:5
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
             resources: ioport:e100-e1ff ioport:e200-e27f iomemory:ec001000-ec001fff irq:11
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
           *-multimedia
                description: Multimedia controller
                product: SAA7133 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 9
                bus info: pci@01:09.0
                version: f0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=saa7134
                resources: iomemory:eb011000-eb0117ff irq:5
           *-network
                description: Ethernet interface
                product: RTL-8029(AS)
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@01:0a.0
                logical name: eth1
                version: 00
                serial: 52:54:ab:3e:7e:b7
                width: 32 bits
                clock: 33MHz
                capabilities: ethernet physical
                configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=89.216.133.45 multicast=yes
                resources: ioport:d000-d01f irq:11
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: d
                bus info: pci@01:0d.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:eb010000-eb0107ff ioport:d100-d17f irq:5
        *-ide
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
             resources: ioport:f000-f00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: PIONEER DVD-RW DVR-108
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 1.20
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma4
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-disk:0
                   description: ATA Disk
                   product: WDC WD800JB-00FMA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 13.03G13
                   serial: WD-WMAJ96850087
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 10001MB
                      capabilities: primary bootable
                 *-volume:1
                      description: W95 Ext'd (LBA) partition
                      physical id: 2
                      bus info: ide@1.0,2
                      logical name: /dev/hdc2
                      capacity: 64GB
                      capabilities: primary
              *-disk:1
                   description: ATA Disk
                   product: WDC WD800JB-00ETA0
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 77.07W77
                   serial: WD-WCAHL2636708
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@1.1,1
                      logical name: /dev/hdd1
                      capacity: 74GB
                      capabilities: primary bootable
                 *-volume:1
                      description: W95 Ext'd (LBA) partition
                      physical id: 3
                      bus info: ide@1.1,3
                      logical name: /dev/hdd3
                      capacity: 8032KB
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
           *-display
                description: VGA compatible controller
                product: NV40.2 [GeForce 6800 LE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@02:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:e8000000-e8ffffff iomemory:e0000000-e7ffffff iomemory:e9000000-e9ffffff irq:9

```

I noticed that it says I have a "nvidia-nForce'  mainboard. This is probably because I haven't installed nVidia's official driver. I have Epox 8RDA3+ PRO.

I hope you can help me :).

---

### Post by yu_raider on 2006-12-29
Nobody knows the solution? :(

---

### Post by Yoooder on 2007-01-16
I just downloaded my first Ubunto CD (not a newb to Linux though) and booted into the LiveCD only to find that all my USB devices are not working as well.

I also have an Epox 8RDA3+ motherboard, which is an nForce2 chipset.  I've had issues in other distros with getting some of it's drivers to work--but not USB to the best of my recollection.

I hope there's a quick and simple fix for this, this machine is going to be my MythTV box and I wanted to give Ubuntu a spin on it (not to mention I don't want to wait for Gentoo to install, I want MythTV NOW :twisted: )

---

### Post by Yoooder on 2007-01-18
TRY THIS!

I have a USB keyboard & mouse, and both were dead in the water with my first load of the Ubuntu LiveCD.  However, I was messing around and gave it a second shot--this time tapping my Num Lock key all the way through the boot (waiting for it to fail to give me a very rough idea of when it was ceasing to function during boot).  It never failed!

I've duplicated this on my machine several times.  If I boot from the LiveCD and do nothing with my keyboard USB fails to work, if I keep tapping that button (maybe once a second or so) everything loads fine.

The good news is that after I ran Install from the LiveCD Ubuntu came up and ran like a charm--the only driver I need to get loaded is the nForce2's audio driver (which has always been a pain for me).

---

