---
title: "Only 3GiB or RAM show up eventhough 4GiB are installed"
date: 2009-06-10
forum: Hardware
---

### Post by lars25700 on 2009-06-10
Just wondering whether anyone else had this problem: 

I have 4GiB of RAM installed and they show up in the BIOS during boot. 

Yet when I hit System > Administration > System Monitor  I only get 3GiB to show up. 

Even if some onboard Graphic chip (my first thought) would eat RAM, it would certainly not be a whole Gig. 

Anyone ever ran across a similar issue?

---

### Post by Gausian on 2009-06-10
I can see 3.4GB on my 32bit laptop.

Maybe your graphics card is reserving mem as shared mem.  lots of integrated cards share mem with RAM to make up for lack of own capacity.

---

### Post by mgmiller on 2009-06-10
If you have 32 bit Ubuntu installed it can only address a bit over 3 gig of ram.  Unless you install a tweaked server kernel, 32 bit will never show you more than a little over 3.  If you install the 64 bit version of Ubuntu, all your ram will be seen and used.  I believe the limit for a 64 bit os is 16 EB (exabytes).

---

### Post by jward3010 on 2009-06-10
This pretty much goes for any OS, including Windows, MAC whatever - 32 bit Operating systems are limited in the amount of numbers they can address / crunch and this causes limits on RAM sizes. If you have an AMD64 processor you can install a 64 bit version of ubuntu and have all the RAM available for use. Go to terminal and type: ```
sudo lshw
``` and post here what comes out, we'll tell you whether you can use 64 bit Ubuntu.

---

### Post by lars25700 on 2010-01-09
> **jward3010 said:**
> This pretty much goes for any OS, including Windows, MAC whatever - 32 bit Operating systems are limited in the amount of numbers they can address / crunch and this causes limits on RAM sizes. If you have an AMD64 processor you can install a 64 bit version of ubuntu and have all the RAM available for use. Go to terminal and type: ```
sudo lshw
``` and post here what comes out, we'll tell you whether you can use 64 bit Ubuntu.

This is what it coughs up: 

```
    description: Mini Tower Computer
    product: D2841-A1
    vendor: FUJITSU SIEMENS
    serial: 255761202
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=2 uuid=DAC0FDDC-8AFA-39B0-C3B1-0019995EE718
  *-core
       description: Motherboard
       product: D2841-A1
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: S26361-D2841-A1
       serial: 29571804
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
          physical id: 0
          version: 6.00 R1.00-01.2841.A1 (02/02/2009)
          size: 99KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 1200MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 8MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 202020202020202020202020202020202020
             vendor: Kingston
             physical id: 0
             serial: 38CCDBD1
             slot: Slot-1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 202020202020202020202020202020202020
             vendor: Kingston
             physical id: 1
             serial: 5CCCD8D1
             slot: Slot-2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:2000(size=4096) memory:dd000000-dfffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9500 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:dd000000-ddffffff memory:e0000000-efffffff(prefetchable) memory:de000000-dfffffff ioport:2000(size=128)
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:20 memory:fc300000-fc303fff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:fc200000-fc2fffff
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 10
                serial: 00:19:99:5e:e7:18
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=192.168.0.135 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:27 memory:fc200000-fc20ffff
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1820(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: Generic USB Hub
                   vendor: ALCOR
                   physical id: 1
                   bus info: usb@2:1
                   version: 3.12
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Mouse
                      product: USB-PS/2 Optical Mouse
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 27.20
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
                 *-usb:1
                      description: Keyboard
                      product: Cymotion Master Linux Keyboard
                      vendor: Cherry GmbH
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 0.32
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fc304000-fc3043ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.31-17-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: USB Hub
                   vendor: Alcor Micro Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18c0(size=16) memory:c0000000-c00003ff
           *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAT22798954
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ec5fa
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 98886e3c-a047-4dce-b94a-e375a746cd1a
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-05-03 18:43:33 filesystem=ext3 modified=2009-12-10 08:35:13 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2010-01-09 01:50:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 125GiB
                   capacity: 125GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5718MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 120GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22NS40
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: NL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1100(size=32)
  *-power UNCLAIMED
       physical id: 1
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

I have checked and disabled the internal graphics stuff - all of it. Only running on my PCIe Graphics Card now.

---

### Post by hfdragon on 2010-01-10
You can use the -pae kernels (search synaptic with -pae).

PAE stands for : Physical Address Extension and is the workaround to be able to use more than 3GiB on a 32bits kernel.

But nowdays, the best solution seems to be using the 64bits kernels.

---

### Post by Cheesemill on 2010-01-10
> **lars25700 said:**
> This is what it coughs up: 

```
    description: Mini Tower Computer
    product: D2841-A1
    vendor: FUJITSU SIEMENS
    serial: 255761202
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=2 uuid=DAC0FDDC-8AFA-39B0-C3B1-0019995EE718
  *-core
       description: Motherboard
       product: D2841-A1
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: S26361-D2841-A1
       serial: 29571804
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
          physical id: 0
          version: 6.00 R1.00-01.2841.A1 (02/02/2009)
          size: 99KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 1200MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 8MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 202020202020202020202020202020202020
             vendor: Kingston
             physical id: 0
             serial: 38CCDBD1
             slot: Slot-1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 202020202020202020202020202020202020
             vendor: Kingston
             physical id: 1
             serial: 5CCCD8D1
             slot: Slot-2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:2000(size=4096) memory:dd000000-dfffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9500 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:dd000000-ddffffff memory:e0000000-efffffff(prefetchable) memory:de000000-dfffffff ioport:2000(size=128)
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:20 memory:fc300000-fc303fff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:fc200000-fc2fffff
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 10
                serial: 00:19:99:5e:e7:18
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=192.168.0.135 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:27 memory:fc200000-fc20ffff
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1820(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: Generic USB Hub
                   vendor: ALCOR
                   physical id: 1
                   bus info: usb@2:1
                   version: 3.12
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Mouse
                      product: USB-PS/2 Optical Mouse
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 27.20
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
                 *-usb:1
                      description: Keyboard
                      product: Cymotion Master Linux Keyboard
                      vendor: Cherry GmbH
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 0.32
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.31-17-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fc304000-fc3043ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.31-17-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: USB Hub
                   vendor: Alcor Micro Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18c0(size=16) memory:c0000000-c00003ff
           *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAT22798954
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ec5fa
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 98886e3c-a047-4dce-b94a-e375a746cd1a
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-05-03 18:43:33 filesystem=ext3 modified=2009-12-10 08:35:13 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2010-01-09 01:50:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 125GiB
                   capacity: 125GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5718MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 120GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22NS40
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: NL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1100(size=32)
  *-power UNCLAIMED
       physical id: 1
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```I have checked and disabled the internal graphics stuff - all of it. Only running on my PCIe Graphics Card now.

Your processor is 64-bit :)

Also your graphics card memory gets taken into account for the 4GB limit, whether it's onboard or an add in card.

---

