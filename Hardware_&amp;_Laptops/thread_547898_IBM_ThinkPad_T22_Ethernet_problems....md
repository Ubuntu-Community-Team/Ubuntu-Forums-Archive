---
title: "IBM ThinkPad T22 Ethernet problems..."
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by bobleny on 2007-09-10
OS: Kubuntu 6.10 Edgy Eft
Install Date: 09-09-07
Upgraded: Kubuntu 7.04 Feisty Fawn
Upgrade Date: 09-12-07
Computer: IBM ThinkPad - Model T22

Here's the problem-
The built in Ethernet card is not registering in the Network Interfaces area. If the computer doesn't know the card is there, I cant use it to connect to the Internet. This is not a new Ethernet card and it worked before when this thing was running Windows 98 SE.

Currently, I am using a linksys wireless usb thingy to connect to the internet......

My question: What do I do?
--------------

Other info:

ifconfig:
```

root@rachels-laptop:/# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1020 (1020.0 b)  TX bytes:1020 (1020.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:0C:41:69:9F:DA
          inet6 addr: fe80::20c:41ff:fe69:9fda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:206025 (201.1 KiB)  TX bytes:0 (0.0 b)

rausb0:av Link encap:Ethernet  HWaddr 00:0C:41:69:9F:DA
          inet addr:169.254.8.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

root@rachels-laptop:/#

```

lshw -C network
```

root@rachels-laptop:/# lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: rausb0
       serial: 00:0c:41:69:9f:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168.1.101 link=yes multicast=yes wireless=RT2500USB WLAN
root@rachels-laptop:/#

```

lshw
```

root@rachels-laptop:/# lshw
rachels-laptop
    description: Notebook
    product: 2647SFM
    vendor: IBM
    version: Not Available
    serial: 786RN3A
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=F5C99801-43F1-11CB-BEB9-A461C573BB33
  *-core
       description: Motherboard
       product: 2647SFM
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1JTU1981XP
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 16ET20WW (1.00b) (03/07/2001)
          size: 144KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.8.10
          slot: None
          size: 900MHz
          capacity: 900MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 256MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 13
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
                resources: iomemory:f0000000-f7ffffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1450
             vendor: Texas Instruments
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: iomemory:50000000-50000fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1450
             vendor: Texas Instruments
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: iomemory:50100000-50100fff irq:11
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: 3
             bus info: pci@00:03.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0 maxlatency=14 mingnt=252
             resources: iomemory:e8101000-e81010ff ioport:1c00-1c07 ioport:1800-18ff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]
             vendor: Cirrus Logic
             physical id: 5
             bus info: pci@00:05.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Sound Fusion CS46xx latency=64 maxlatency=24 mingnt=4
             resources: iomemory:e8100000-e8100fff iomemory:e8000000-e80fffff irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=64
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:1c10-1c1f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IBM-DJSA-232
                   vendor: IBM
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: JS8IAD1A
                   serial: 48YBWLM6460
                   size: 29GB
                   capacity: 29GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 29GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 721MB
                      capacity: 721MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 721MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: MATSHITADVD-ROM SR-8175
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: G228
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64
             resources: ioport:1c20-1c3f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: Wireless-G USB Network Adapter
                   vendor: Cisco-Linksys
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.04
                   capabilities: usb-2.00
                   configuration: driver=rt2570 maxpower=300mA speed=12.0MB/s
        *-bridge:1 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
             resources: irq:9
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: rausb0
       serial: 00:0c:41:69:9f:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168.1.101 link=yes multicast=yes wireless=RT2500USB WLAN
root@rachels-laptop:/#

```


Thanks!

---

### Post by bobleny on 2007-09-11
Any ideas?

Maybe I just need a driver for it?

Where can I get drivers, or the Linux equivalent?

---

### Post by bobleny on 2007-09-15
I was hoping that if I upgraded to 7.04, something might be different and it would magically appear. It didn't....

Anyways, I am still sitting here in the dark looking up posts of a similar problem, and trying to fix this stupid thing....

So, if you have any suggestions or idea on what I can do, please don't hesitate to ask!

Oh, and I have updated the thread for the changes that occurred with 7.04.

Thanks!

---

