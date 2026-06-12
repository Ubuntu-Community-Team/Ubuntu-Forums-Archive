---
title: "IDE devices not recognized"
date: 2009-11-29
forum: Hardware
---

### Post by RRockon on 2009-11-29
I've recently installed 9.10 on my system, along side an existing Windows. Everything seems to work pretty well, except that ubuntu doesn't see any of the IDE devices I have on this machine, which windows does see.

This was already an issue with the installation, I was unable to install or even boot from a livecd. It just kicked me into a 'busybox'. I had to use an USB device to install and now that it's working I can't access my CD/DVD drive or my secondary (IDE) Hard-disk. My primary one is a SATA and works fine.

I'm relatively new to linux/ubuntu and I have no clue what to do. Any help would be much appreciated!

---

### Post by chrisfu on 2009-11-29
> **RRockon said:**
> I've recently installed 9.10 on my system, along side an existing Windows. Everything seems to work pretty well, except that ubuntu doesn't see any of the IDE devices I have on this machine, which windows does see.

This was already an issue with the installation, I was unable to install or even boot from a livecd. It just kicked me into a 'busybox'. I had to use an USB device to install and now that it's working I can't access my CD/DVD drive or my secondary (IDE) Hard-disk. My primary one is a SATA and works fine.

I'm relatively new to linux/ubuntu and I have no clue what to do. Any help would be much appreciated!

What's the output of 'sudo lspci' and 'sudo lshw'?

---

### Post by RRockon on 2009-11-29
**lspci**

```
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
02:00.1 IDE interface: VIA Technologies, Inc. PATA IDE Host Controller (rev a0)
03:00.0 SATA controller: JMicron Technology Corp. JMB360 AHCI Controller (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)

```**lshw**

```

shredder
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: X58 Extreme
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30 (07/16/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.10.5
          serial: 0001-06A5-0000-0000-0000-0000
          slot: CPUSocket
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology tsc_reliable nonstop_tsc pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns)
             product: CM3X2G1600C9
             vendor: Corsair
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns) [empty]
             vendor: Manufacturer01
             physical id: 1
             serial: 00000000
             slot: DIMM1
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0.8 ns)
             vendor: Manufacturer02
             physical id: 2
             serial: 00000000
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM 1333 MHz (0.8 ns) [empty]
             product: CM3X2G1600C9
             vendor: Corsair
             physical id: 3
             serial: 00000000
             slot: DIMM3
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:4
             description: DIMM 1333 MHz (0.8 ns)
             vendor: Manufacturer04
             physical id: 4
             serial: 00000000
             slot: DIMM4
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:5
             description: DIMM 1333 MHz (0.8 ns) [empty]
             vendor: Manufacturer05
             physical id: 5
             serial: 00000000
             slot: DIMM5
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: X58 I/O Hub to ESI Port
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:e000(size=4096) memory:f9000000-fbefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f9000000-f9ffffff ioport:ec00(size=128) memory:fb000000-fb01ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26
        *-generic:0 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub System Management Registers
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Control Status and RAS Registers
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Throttle Registers
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:8400(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:8480(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:8800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f8cf6000-f8cf63ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f8cf8000-f8cfbfff
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:d000(size=4096) memory:f8f00000-f8ffffff
           *-storage
                description: SATA controller
                product: JMB360 AHCI Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:16 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:f8ffe000-f8ffffff
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:28 ioport:c000(size=4096) memory:f8e00000-f8efffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:17 memory:f8eef800-f8eeffff ioport:c000(size=256)
           *-ide UNCLAIMED
                description: IDE interface
                product: PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a0
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16) memory:f8ef0000-f8efffff(prefetchable)
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:29 ioport:b000(size=4096) memory:f8d00000-f8dfffff ioport:cff00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 03
                serial: 00:19:66:ee:2e:38
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.29 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:30 ioport:b800(size=256) memory:cffff000-cfffffff(prefetchable) memory:cfff8000-cfffbfff(prefetchable) memory:f8de0000-f8dfffff(prefetchable)
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:8880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:8c00(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:9000(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8cfc000-f8cfc3ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:9c00(size=8) ioport:9880(size=4) ioport:9800(size=8) ioport:9480(size=4) ioport:9400(size=16) ioport:9080(size=16)
           *-disk
                description: ATA Disk
                product: STM31000528AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: CC35
                serial: 9VP0RRV8
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f778f778
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/windisk
                   version: 3.1
                   serial: 96278357-74c8-d241-95cb-ff9994b3a8fb
                   size: 516GiB
                   capacity: 516GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-09-09 19:58:18 filesystem=ntfs label=HD modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 9e0b1f3e-5fa6-4495-93e6-d27532345f1a
                   size: 5106MiB
                   capacity: 5106MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 24987c36-5a1c-49b8-94be-54705e9ac2d8
                   size: 410GiB
                   capacity: 410GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-11-16 21:43:55 filesystem=ext3 modified=2009-11-26 18:44:18 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2009-11-29 22:19:16 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f8cfe000-f8cfe0ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=8) ioport:a480(size=4) ioport:a400(size=16) ioport:a080(size=16)

```

---

### Post by chrisfu on 2009-11-29
> **RRockon said:**
> 
           *-ide UNCLAIMED
                description: IDE interface
                product: PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a0
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16) memory:f8ef0000-f8efffff(prefetchable)


Hmmm, sounds like you have a VT6330 chip on your motherboard.  What brand and model is the board?  If you check the board you should see a chip exactly like this on it:

[IMG]http://farm3.static.flickr.com/2226/2356723839_6ce264e504.jpg[/IMG]

The [VT6330]("http://www.via.com.tw/en/products/peripherals/1394/vt6330/") is a hybrid chip to cut costs.  It handles PATA IDE and and firewire.   The firewire functionality is identical to that of the [VT6315S]("http://www.via.com.tw/en/products/peripherals/1394/vt6315/") chip they produce to handle that, which is why your firewire is working and not listed as unclaimed.

The PATA IDE functionality is *supposed* to be identical to that of the [VT6415]("http://www.via.com.tw/en/products/peripherals/pci_pcie/vt6415/") (which has been supported since 2.6.28), but alas there was one tiny, tiny difference which meant that it doesn't work.  It is detected during boot, but the module that's supposed to work with it, outright rejects it.

I reported this to VIA around 5 weeks ago with suggested fix, and they have since had a patch accepted into the 2.6.32 kernel tree.  The Ubuntu Kernel team have also implemented this fix (amongst 100 or so other fixes) into 2.6.31-16 which is due to appear in karmic-proposed in the next week or so.

A working pre-release version of this kernel is available now from [https://launchpad.net/~stefan-bader-canonical/+archive/karmic](https://launchpad.net/~stefan-bader-canonical/+archive/karmic).  Give that a shot and let me know how it works out for you!  It's just a new apt source containing that kernel, and so won't interfere with your system at all.

Chris

---

### Post by RRockon on 2009-11-30
I tried the new kernel and it fixes the IDE troubles completely! Guess I'll wait for next week for the 'definitive' version. It's not a major thing right now... and I had to disable the Nvidia drivers to get an X started. Probably something simple, but I didn't feel it was worth the effort to tinker with that when it's likely to not be an issue next week on release.

Thanks for the heads-up!

---

### Post by chrisfu on 2009-11-30
> **RRockon said:**
> I tried the new kernel and it fixes the IDE troubles completely! Guess I'll wait for next week for the 'definitive' version. It's not a major thing right now... and I had to disable the Nvidia drivers to get an X started. Probably something simple, but I didn't feel it was worth the effort to tinker with that when it's likely to not be an issue next week on release.

Thanks for the heads-up!

Glad that it worked for you. :)  Installing it should have really compiled the Nvidia modules really, but I imagine it'll be an issue that's ironed out when it's released properly.

It's not guaranteed to be released next week, but judging by when it was announced on the kernel team mailing list and the usual cycle, that's when I'd expect to see it hit karmic-proposed. :)

---

### Post by oni5115 on 2009-12-05
Are there any live distros with a kernal that supports that chip?  My HD has 4 more days until it arrives... and I wanna play with my new PC.

---

### Post by chrisfu on 2009-12-05
> **oni5115 said:**
> Are there any live distros with a kernal that supports that chip?  My HD has 4 more days until it arrives... and I wanna play with my new PC.

No Live CD's as far as I know I'm afraid.

RRockon, 2.6.31-16 appears to have skipped proposed and gone straight into updates.  I've tried it, but for some reason my IDE has now stopped working... have you updated yet?  EDIT: In fact, stay away from it for now if you want to keep current IDE functionality.  It doesn't include the proposed changes, seemingly because the kernel team needed to rush some security updates/kitten-killer bug-fixes.

---

### Post by oni5115 on 2009-12-05
Good to know.  For now I just went and created a USB stick to play with.  That's been working just fine - aside from it being 32 bit and capping my ram to 3 Gb.  I can live with that though for the next few days.

---

### Post by goremache on 2009-12-06
hi,
I'm dealing with the same problem.
I have a ide old MAXTOR drive that is not visible on an new ASROCK P55M Pro that has this chip on board. I have installed a 9.10 amd64 version. In the system I have a SATA drive that works without any problems. 
Also I have applied today updates.
Here is my syslog after the packs from today.

```

Dec  6 15:14:49 weasel kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec  6 15:14:49 weasel rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="813" x-info="http://www.rsyslog.com"] (re)start
Dec  6 15:14:49 weasel rsyslogd: rsyslogd's groupid changed to 102
Dec  6 15:14:50 weasel rsyslogd: rsyslogd's userid changed to 101
Dec  6 15:14:50 weasel NetworkManager: <info>  starting...
Dec  6 15:14:50 weasel NetworkManager: <info>  Trying to start the modem-manager...
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: init!
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Dec  6 15:14:50 weasel NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0)
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: end _init.
Dec  6 15:14:50 weasel NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Ericsson MBM
Dec  6 15:14:50 weasel avahi-daemon[829]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Dec  6 15:14:50 weasel kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  6 15:14:50 weasel kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  6 15:14:50 weasel kernel: [    0.000000] Linux version 2.6.31-16-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 (Ubuntu 2.6.31-16.52-generic)
Dec  6 15:14:50 weasel kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=58b7b0b4-91e3-4c57-89b2-74bac7864aa8 ro quiet splash
Dec  6 15:14:50 weasel kernel: [    0.000000] KERNEL supported cpus:
Dec  6 15:14:50 weasel kernel: [    0.000000]   Intel GenuineIntel
Dec  6 15:14:50 weasel kernel: [    0.000000]   AMD AuthenticAMD
Dec  6 15:14:50 weasel kernel: [    0.000000]   Centaur CentaurHauls
Dec  6 15:14:50 weasel kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cb770000 (usable)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000cb770000 - 00000000cb780000 (ACPI data)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000cb780000 - 00000000cb7d0000 (ACPI NVS)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000cb7d0000 - 00000000cb7e0000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000cb7eb400 - 00000000cc000000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000] DMI present.
Dec  6 15:14:50 weasel kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec  6 15:14:50 weasel kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000] last_pfn = 0xcb770 max_arch_pfn = 0x400000000
Dec  6 15:14:50 weasel avahi-daemon[829]: Successfully dropped root privileges.
Dec  6 15:14:50 weasel kernel: [    0.000000] MTRR default type: uncachable
Dec  6 15:14:50 weasel kernel: [    0.000000] MTRR fixed ranges enabled:
Dec  6 15:14:50 weasel kernel: [    0.000000]   00000-9FFFF write-back
Dec  6 15:14:50 weasel kernel: [    0.000000]   A0000-BFFFF uncachable
Dec  6 15:14:50 weasel kernel: [    0.000000]   C0000-CFFFF write-protect
Dec  6 15:14:50 weasel kernel: [    0.000000]   D0000-DFFFF uncachable
Dec  6 15:14:50 weasel kernel: [    0.000000]   E0000-EBFFF write-through
Dec  6 15:14:50 weasel kernel: [    0.000000]   EC000-FFFFF write-protect
Dec  6 15:14:50 weasel kernel: [    0.000000] MTRR variable ranges enabled:
Dec  6 15:14:50 weasel kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Dec  6 15:14:50 weasel kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Dec  6 15:14:50 weasel kernel: [    0.000000]   2 base 0C0000000 mask FF8000000 write-back
Dec  6 15:14:50 weasel kernel: [    0.000000]   3 base 0C8000000 mask FFC000000 write-back
Dec  6 15:14:50 weasel kernel: [    0.000000]   4 disabled
Dec  6 15:14:50 weasel kernel: [    0.000000]   5 disabled
Dec  6 15:14:50 weasel kernel: [    0.000000]   6 disabled
Dec  6 15:14:50 weasel kernel: [    0.000000]   7 disabled
Dec  6 15:14:50 weasel kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec  6 15:14:50 weasel kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec  6 15:14:50 weasel kernel: [    0.000000] modified physical RAM map:
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 0000000000100000 - 00000000cb770000 (usable)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000cb770000 - 00000000cb780000 (ACPI data)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000cb780000 - 00000000cb7d0000 (ACPI NVS)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000cb7d0000 - 00000000cb7e0000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000cb7eb400 - 00000000cc000000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec  6 15:14:50 weasel kernel: [    0.000000]  modified: 00000000ffa00000 - 0000000100000000 (reserved)
Dec  6 15:14:50 weasel modem-manager: Loaded plugin MotoC
Dec  6 15:14:50 weasel kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec  6 15:14:50 weasel kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cb770000
Dec  6 15:14:50 weasel kernel: [    0.000000] Warning: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
Dec  6 15:14:50 weasel kernel: [    0.000000]  0000000000 - 00cb600000 page 2M
Dec  6 15:14:50 weasel kernel: [    0.000000]  00cb600000 - 00cb770000 page 4k
Dec  6 15:14:50 weasel kernel: [    0.000000] kernel direct mapping tables up to cb770000 @ 10000-16000
Dec  6 15:14:50 weasel kernel: [    0.000000] RAMDISK: 3786c000 - 37fef38f
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: RSDP 00000000000fa8c0 00014 (v00 ACPIAM)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: RSDT 00000000cb770000 00044 (v01 081309 RSDT2052 20090813 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: FACP 00000000cb770200 00084 (v01 A_M_I  OEMFACP  12000601 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: DSDT 00000000cb770460 06F9E (v01  AS252 AS252028 00000028 INTL 20051117)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: FACS 00000000cb780000 00040
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: APIC 00000000cb770390 0008C (v01 081309 APIC2052 20090813 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: MCFG 00000000cb770420 0003C (v01 081309 OEMMCFG  20090813 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: OEMB 00000000cb780040 00073 (v01 081309 OEMB2052 20090813 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: AAFT 00000000cb77a460 00027 (v01 081309 OEMAAFT  20090813 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: GSCI 00000000cb7800c0 02024 (v01 081309 GMCHSCI  20090813 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: DMAR 00000000cb7820f0 000F0 (v01    AMI  OEMDMAR 00000001 MSFT 00000097)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: SSDT 00000000cb7837f0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  6 15:14:50 weasel kernel: [    0.000000] No NUMA configuration found
Dec  6 15:14:50 weasel kernel: [    0.000000] Faking a node at 0000000000000000-00000000cb770000
Dec  6 15:14:50 weasel kernel: [    0.000000] Bootmem setup node 0 0000000000000000-00000000cb770000
Dec  6 15:14:50 weasel kernel: [    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
Dec  6 15:14:50 weasel kernel: [    0.000000]   bootmap [0000000000019000 -  00000000000326ef] pages 1a
Dec  6 15:14:50 weasel kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00cb770000]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #3 [003786c000 - 0037fef38f]          RAMDISK ==> [003786c000 - 0037fef38f]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #5 [00019e5000 - 00019e512f]              BRK ==> [00019e5000 - 00019e512f]
Dec  6 15:14:50 weasel kernel: [    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
Dec  6 15:14:50 weasel kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Dec  6 15:14:50 weasel kernel: [    0.000000]  [ffffea0000000000-ffffea0002dfffff] PMD -> [ffff880001e00000-ffff880004bfffff] on node 0
Dec  6 15:14:50 weasel kernel: [    0.000000] Zone PFN ranges:
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec  6 15:14:50 weasel kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Dec  6 15:14:50 weasel kernel: [    0.000000] Movable zone start PFN for each node
Dec  6 15:14:50 weasel kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec  6 15:14:50 weasel kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec  6 15:14:50 weasel kernel: [    0.000000]     0: 0x00000100 -> 0x000cb770
Dec  6 15:14:50 weasel kernel: [    0.000000] On node 0 totalpages: 833279
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA zone: 103 pages reserved
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA zone: 3824 pages, LIFO batch:0
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Generic
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA32 zone: 11339 pages used for memmap
Dec  6 15:14:50 weasel kernel: [    0.000000]   DMA32 zone: 817957 pages, LIFO batch:31
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
Dec  6 15:14:50 weasel kernel: [    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec  6 15:14:50 weasel kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  6 15:14:50 weasel kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  6 15:14:50 weasel kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Dec  6 15:14:50 weasel kernel: [    0.000000] nr_irqs_gsi: 24
Dec  6 15:14:50 weasel kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec  6 15:14:50 weasel kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec  6 15:14:50 weasel kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec  6 15:14:50 weasel kernel: [    0.000000] Allocating PCI resources starting at cc000000 (gap: cc000000:32e00000)
Dec  6 15:14:50 weasel kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
Dec  6 15:14:50 weasel kernel: [    0.000000] PERCPU: Embedded 30 pages at ffff880001a02000, static data 90720 bytes
Dec  6 15:14:50 weasel kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 821781
Dec  6 15:14:50 weasel kernel: [    0.000000] Policy zone: DMA32
Dec  6 15:14:50 weasel avahi-daemon[829]: avahi-daemon 0.6.25 starting up.
Dec  6 15:14:50 weasel kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=58b7b0b4-91e3-4c57-89b2-74bac7864aa8 ro quiet splash
Dec  6 15:14:50 weasel kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Dec  6 15:14:50 weasel kernel: [    0.000000] Initializing CPU#0
Dec  6 15:14:50 weasel kernel: [    0.000000] Checking aperture...
Dec  6 15:14:50 weasel kernel: [    0.000000] No AGP bridge found
Dec  6 15:14:50 weasel kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec  6 15:14:50 weasel kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec  6 15:14:50 weasel kernel: [    0.000000] Memory: 3267008k/3333568k available (5315k kernel code, 452k absent, 66108k reserved, 3018k data, 660k init)
Dec  6 15:14:50 weasel kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Dec  6 15:14:50 weasel kernel: [    0.000000] NR_IRQS:4352 nr_irqs:472
Dec  6 15:14:50 weasel kernel: [    0.000000] Fast TSC calibration using PIT
Dec  6 15:14:50 weasel kernel: [    0.000000] Detected 2667.046 MHz processor.
Dec  6 15:14:50 weasel kernel: [    0.001471] Console: colour VGA+ 80x25
Dec  6 15:14:50 weasel kernel: [    0.001473] console [tty0] enabled
Dec  6 15:14:50 weasel kernel: [    0.009229] allocated 34078720 bytes of page_cgroup
Dec  6 15:14:50 weasel kernel: [    0.009231] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec  6 15:14:50 weasel kernel: [    0.009262] Calibrating delay loop (skipped), value calculated using timer frequency.. 5334.09 BogoMIPS (lpj=26670460)
Dec  6 15:14:50 weasel kernel: [    0.009277] Security Framework initialized
Dec  6 15:14:50 weasel kernel: [    0.009290] AppArmor: AppArmor initialized
Dec  6 15:14:50 weasel kernel: [    0.009535] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec  6 15:14:50 weasel kernel: [    0.010464] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec  6 15:14:50 weasel kernel: [    0.010826] Mount-cache hash table entries: 256
Dec  6 15:14:50 weasel kernel: [    0.010906] Initializing cgroup subsys ns
Dec  6 15:14:50 weasel kernel: [    0.010909] Initializing cgroup subsys cpuacct
Dec  6 15:14:50 weasel kernel: [    0.010911] Initializing cgroup subsys memory
Dec  6 15:14:50 weasel kernel: [    0.010915] Initializing cgroup subsys freezer
Dec  6 15:14:50 weasel kernel: [    0.010916] Initializing cgroup subsys net_cls
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Huawei
Dec  6 15:14:50 weasel kernel: [    0.010925] CPU: Physical Processor ID: 0
Dec  6 15:14:50 weasel kernel: [    0.010926] CPU: Processor Core ID: 0
Dec  6 15:14:50 weasel modem-manager: Loaded plugin ZTE
Dec  6 15:14:50 weasel kernel: [    0.010929] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec  6 15:14:50 weasel kernel: [    0.010931] CPU: L2 cache: 256K
Dec  6 15:14:50 weasel kernel: [    0.010932] CPU: L3 cache: 8192K
Dec  6 15:14:50 weasel kernel: [    0.010934] CPU 0/0x0 -> Node 0
Dec  6 15:14:50 weasel kernel: [    0.010936] mce: CPU supports 9 MCE banks
Dec  6 15:14:50 weasel kernel: [    0.010945] CPU0: Thermal monitoring enabled (TM1)
Dec  6 15:14:50 weasel kernel: [    0.010948] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 SHD:8
Dec  6 15:14:50 weasel kernel: [    0.010955] using mwait in idle threads.
Dec  6 15:14:50 weasel kernel: [    0.010956] Performance Counters: Nehalem/Corei7 events, Intel PMU driver.
Dec  6 15:14:50 weasel kernel: [    0.010959] ... version:                 3
Dec  6 15:14:50 weasel kernel: [    0.010960] ... bit width:               48
Dec  6 15:14:50 weasel kernel: [    0.010961] ... generic counters:        4
Dec  6 15:14:50 weasel kernel: [    0.010962] ... value mask:              0000ffffffffffff
Dec  6 15:14:50 weasel kernel: [    0.010964] ... max period:              000000007fffffff
Dec  6 15:14:50 weasel kernel: [    0.010965] ... fixed-purpose counters:  3
Dec  6 15:14:50 weasel kernel: [    0.010966] ... counter mask:            000000070000000f
Dec  6 15:14:50 weasel kernel: [    0.012633] ACPI: Core revision 20090521
Dec  6 15:14:50 weasel kernel: [    0.041858] Setting APIC routing to flat
Dec  6 15:14:50 weasel kernel: [    0.042184] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec  6 15:14:50 weasel kernel: [    0.141946] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
Dec  6 15:14:50 weasel kernel: [    0.258716] Booting processor 1 APIC 0x2 ip 0x6000
Dec  6 15:14:50 weasel kernel: [    0.271065] Initializing CPU#1
Dec  6 15:14:50 weasel kernel: [    0.418220] Calibrating delay using timer specific routine.. 5333.53 BogoMIPS (lpj=26667660)
Dec  6 15:14:50 weasel kernel: [    0.418226] CPU: Physical Processor ID: 0
Dec  6 15:14:50 weasel kernel: [    0.418227] CPU: Processor Core ID: 1
Dec  6 15:14:50 weasel kernel: [    0.418229] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec  6 15:14:50 weasel kernel: [    0.418230] CPU: L2 cache: 256K
Dec  6 15:14:50 weasel kernel: [    0.418231] CPU: L3 cache: 8192K
Dec  6 15:14:50 weasel kernel: [    0.418233] CPU 1/0x2 -> Node 0
Dec  6 15:14:50 weasel kernel: [    0.418235] mce: CPU supports 9 MCE banks
Dec  6 15:14:50 weasel kernel: [    0.418243] CPU1: Thermal monitoring enabled (TM1)
Dec  6 15:14:50 weasel kernel: [    0.418246] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Dec  6 15:14:50 weasel kernel: [    0.418879] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Dec  6 15:14:50 weasel kernel: [    0.419455] CPU1: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
Dec  6 15:14:50 weasel kernel: [    0.419463] Skipping synchronization checks as TSC is reliable.
Dec  6 15:14:50 weasel kernel: [    0.419527] Booting processor 2 APIC 0x4 ip 0x6000
Dec  6 15:14:50 weasel kernel: [    0.431347] Initializing CPU#2
Dec  6 15:14:50 weasel kernel: [    0.577808] Calibrating delay using timer specific routine.. 5333.53 BogoMIPS (lpj=26667680)
Dec  6 15:14:50 weasel kernel: [    0.577814] CPU: Physical Processor ID: 0
Dec  6 15:14:50 weasel kernel: [    0.577815] CPU: Processor Core ID: 2
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Option High-Speed
Dec  6 15:14:50 weasel kernel: [    0.577817] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec  6 15:14:50 weasel kernel: [    0.577819] CPU: L2 cache: 256K
Dec  6 15:14:50 weasel kernel: [    0.577819] CPU: L3 cache: 8192K
Dec  6 15:14:50 weasel kernel: [    0.577821] CPU 2/0x4 -> Node 0
Dec  6 15:14:50 weasel kernel: [    0.577823] mce: CPU supports 9 MCE banks
Dec  6 15:14:50 weasel kernel: [    0.577831] CPU2: Thermal monitoring enabled (TM1)
Dec  6 15:14:50 weasel kernel: [    0.577834] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Dec  6 15:14:50 weasel kernel: [    0.578468] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
Dec  6 15:14:50 weasel kernel: [    0.579081] CPU2: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
Dec  6 15:14:50 weasel kernel: [    0.579088] Skipping synchronization checks as TSC is reliable.
Dec  6 15:14:50 weasel kernel: [    0.579153] Booting processor 3 APIC 0x6 ip 0x6000
Dec  6 15:14:50 weasel kernel: [    0.590895] Initializing CPU#3
Dec  6 15:14:50 weasel kernel: [    0.737397] Calibrating delay using timer specific routine.. 5333.53 BogoMIPS (lpj=26667664)
Dec  6 15:14:50 weasel kernel: [    0.737403] CPU: Physical Processor ID: 0
Dec  6 15:14:50 weasel kernel: [    0.737404] CPU: Processor Core ID: 3
Dec  6 15:14:50 weasel kernel: [    0.737406] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec  6 15:14:50 weasel kernel: [    0.737407] CPU: L2 cache: 256K
Dec  6 15:14:50 weasel kernel: [    0.737408] CPU: L3 cache: 8192K
Dec  6 15:14:50 weasel kernel: [    0.737410] CPU 3/0x6 -> Node 0
Dec  6 15:14:50 weasel kernel: [    0.737412] mce: CPU supports 9 MCE banks
Dec  6 15:14:50 weasel kernel: [    0.737419] CPU3: Thermal monitoring enabled (TM1)
Dec  6 15:14:50 weasel kernel: [    0.737422] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Dec  6 15:14:50 weasel kernel: [    0.738051] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
Dec  6 15:14:50 weasel kernel: [    0.738604] CPU3: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
Dec  6 15:14:50 weasel kernel: [    0.738611] Skipping synchronization checks as TSC is reliable.
Dec  6 15:14:50 weasel kernel: [    0.738625] Brought up 4 CPUs
Dec  6 15:14:50 weasel kernel: [    0.738627] Total of 4 processors activated (21334.69 BogoMIPS).
Dec  6 15:14:50 weasel kernel: [    0.738675] CPU0 attaching sched-domain:
Dec  6 15:14:50 weasel kernel: [    0.738677]  domain 0: span 0-3 level MC
Dec  6 15:14:50 weasel kernel: [    0.738679]   groups: 0 1 2 3
Dec  6 15:14:50 weasel kernel: [    0.738683] CPU1 attaching sched-domain:
Dec  6 15:14:50 weasel kernel: [    0.738684]  domain 0: span 0-3 level MC
Dec  6 15:14:50 weasel kernel: [    0.738685]   groups: 1 2 3 0
Dec  6 15:14:50 weasel kernel: [    0.738689] CPU2 attaching sched-domain:
Dec  6 15:14:50 weasel kernel: [    0.738690]  domain 0: span 0-3 level MC
Dec  6 15:14:50 weasel kernel: [    0.738691]   groups: 2 3 0 1
Dec  6 15:14:50 weasel kernel: [    0.738694] CPU3 attaching sched-domain:
Dec  6 15:14:50 weasel kernel: [    0.738695]  domain 0: span 0-3 level MC
Dec  6 15:14:50 weasel kernel: [    0.738697]   groups: 3 0 1 2
Dec  6 15:14:50 weasel kernel: [    0.738891] Booting paravirtualized kernel on bare hardware
Dec  6 15:14:50 weasel kernel: [    0.739023] regulator: core version 0.5
Dec  6 15:14:50 weasel kernel: [    0.739045] Time: 13:14:40  Date: 12/06/09
Dec  6 15:14:50 weasel kernel: [    0.739077] NET: Registered protocol family 16
Dec  6 15:14:50 weasel kernel: [    0.739156] ACPI: bus type pci registered
Dec  6 15:14:50 weasel kernel: [    0.739202] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec  6 15:14:50 weasel kernel: [    0.739204] PCI: Not using MMCONFIG.
Dec  6 15:14:50 weasel kernel: [    0.739205] PCI: Using configuration type 1 for base access
Dec  6 15:14:50 weasel kernel: [    0.739743] bio: create slab <bio-0> at 0
Dec  6 15:14:50 weasel kernel: [    0.740390] ACPI: EC: Look up EC in DSDT
Dec  6 15:14:50 weasel kernel: [    0.748707] ACPI: Interpreter enabled
Dec  6 15:14:50 weasel kernel: [    0.748710] ACPI: (supports S0 S1 S3 S4 S5)
Dec  6 15:14:50 weasel kernel: [    0.748726] ACPI: Using IOAPIC for interrupt routing
Dec  6 15:14:50 weasel kernel: [    0.748770] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec  6 15:14:50 weasel kernel: [    0.751794] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Dec  6 15:14:50 weasel kernel: [    0.754108] PCI: Using MMCONFIG at e0000000 - efffffff
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Novatel
Dec  6 15:14:50 weasel kernel: [    0.761300] ACPI: No dock devices found.
Dec  6 15:14:50 weasel kernel: [    0.761564] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  6 15:14:50 weasel kernel: [    0.761659] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.761662] pci 0000:00:03.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.761908] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf7df6000-0xf7df63ff]
Dec  6 15:14:50 weasel kernel: [    0.761956] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.761960] pci 0000:00:1a.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.761995] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7df8000-0xf7dfbfff]
Dec  6 15:14:50 weasel kernel: [    0.762031] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762034] pci 0000:00:1b.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762146] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762149] pci 0000:00:1c.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762200] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762203] pci 0000:00:1c.1: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762254] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762257] pci 0000:00:1c.2: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762307] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762310] pci 0000:00:1c.3: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762361] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762364] pci 0000:00:1c.4: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762411] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf7dfc000-0xf7dfc3ff]
Dec  6 15:14:50 weasel kernel: [    0.762460] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.762463] pci 0000:00:1d.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.762614] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
Dec  6 15:14:50 weasel kernel: [    0.762619] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
Dec  6 15:14:50 weasel kernel: [    0.762623] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
Dec  6 15:14:50 weasel kernel: [    0.762628] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
Dec  6 15:14:50 weasel kernel: [    0.762633] pci 0000:00:1f.2: reg 20 io port: [0xff90-0xff9f]
Dec  6 15:14:50 weasel kernel: [    0.762637] pci 0000:00:1f.2: reg 24 io port: [0xffa0-0xffaf]
Dec  6 15:14:50 weasel kernel: [    0.762677] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7dffc00-0xf7dffcff]
Dec  6 15:14:50 weasel kernel: [    0.762688] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Dec  6 15:14:50 weasel kernel: [    0.762725] pci 0000:00:1f.5: reg 10 io port: [0xbc00-0xbc07]
Dec  6 15:14:50 weasel kernel: [    0.762730] pci 0000:00:1f.5: reg 14 io port: [0xb880-0xb883]
Dec  6 15:14:50 weasel kernel: [    0.762735] pci 0000:00:1f.5: reg 18 io port: [0xb800-0xb807]
Dec  6 15:14:50 weasel kernel: [    0.762739] pci 0000:00:1f.5: reg 1c io port: [0xb480-0xb483]
Dec  6 15:14:50 weasel kernel: [    0.762744] pci 0000:00:1f.5: reg 20 io port: [0xb400-0xb40f]
Dec  6 15:14:50 weasel kernel: [    0.762749] pci 0000:00:1f.5: reg 24 io port: [0xb080-0xb08f]
Dec  6 15:14:50 weasel kernel: [    0.762799] pci 0000:07:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
Dec  6 15:14:50 weasel kernel: [    0.762806] pci 0000:07:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
Dec  6 15:14:50 weasel kernel: [    0.762814] pci 0000:07:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
Dec  6 15:14:50 weasel kernel: [    0.762818] pci 0000:07:00.0: reg 24 io port: [0xec00-0xec7f]
Dec  6 15:14:50 weasel kernel: [    0.762823] pci 0000:07:00.0: reg 30 32bit mmio: [0xfaf80000-0xfaffffff]
Dec  6 15:14:50 weasel kernel: [    0.762869] pci 0000:00:03.0: bridge io port: [0xe000-0xefff]
Dec  6 15:14:50 weasel kernel: [    0.762871] pci 0000:00:03.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
Dec  6 15:14:50 weasel kernel: [    0.762875] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Dec  6 15:14:50 weasel kernel: [    0.762915] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xcff00000-0xcfffffff]
Dec  6 15:14:50 weasel kernel: [    0.762962] pci 0000:02:00.0: reg 10 64bit mmio: [0xf7eef800-0xf7eeffff]
Dec  6 15:14:50 weasel kernel: [    0.762969] pci 0000:02:00.0: reg 18 io port: [0xc000-0xc0ff]
Dec  6 15:14:50 weasel kernel: [    0.763023] pci 0000:02:00.0: supports D2
Dec  6 15:14:50 weasel kernel: [    0.763024] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.763028] pci 0000:02:00.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.763082] pci 0000:02:00.1: reg 10 io port: [0xcc00-0xcc07]
Dec  6 15:14:50 weasel kernel: [    0.763089] pci 0000:02:00.1: reg 14 io port: [0xc880-0xc883]
Dec  6 15:14:50 weasel kernel: [    0.763096] pci 0000:02:00.1: reg 18 io port: [0xc800-0xc807]
Dec  6 15:14:50 weasel kernel: [    0.763103] pci 0000:02:00.1: reg 1c io port: [0xc480-0xc483]
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Sierra
Dec  6 15:14:50 weasel kernel: [    0.763110] pci 0000:02:00.1: reg 20 io port: [0xc400-0xc40f]
Dec  6 15:14:50 weasel kernel: [    0.763123] pci 0000:02:00.1: reg 30 32bit mmio: [0xf7ef0000-0xf7efffff]
Dec  6 15:14:50 weasel kernel: [    0.763156] pci 0000:02:00.1: supports D2
Dec  6 15:14:50 weasel kernel: [    0.763157] pci 0000:02:00.1: PME# supported from D2 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.763161] pci 0000:02:00.1: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.763213] pci 0000:00:1c.1: bridge io port: [0xc000-0xcfff]
Dec  6 15:14:50 weasel kernel: [    0.763216] pci 0000:00:1c.1: bridge 32bit mmio: [0xf7e00000-0xf7efffff]
Dec  6 15:14:50 weasel kernel: [    0.763261] pci 0000:04:00.0: reg 10 io port: [0xd800-0xd8ff]
Dec  6 15:14:50 weasel kernel: [    0.763279] pci 0000:04:00.0: reg 18 64bit mmio: [0xcfdff000-0xcfdfffff]
Dec  6 15:14:50 weasel kernel: [    0.763291] pci 0000:04:00.0: reg 20 64bit mmio: [0xcfdf8000-0xcfdfbfff]
Dec  6 15:14:50 weasel kernel: [    0.763299] pci 0000:04:00.0: reg 30 32bit mmio: [0xf7fe0000-0xf7ffffff]
Dec  6 15:14:50 weasel kernel: [    0.763335] pci 0000:04:00.0: supports D1 D2
Dec  6 15:14:50 weasel kernel: [    0.763336] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  6 15:14:50 weasel kernel: [    0.763341] pci 0000:04:00.0: PME# disabled
Dec  6 15:14:50 weasel kernel: [    0.763393] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff]
Dec  6 15:14:50 weasel kernel: [    0.763396] pci 0000:00:1c.2: bridge 32bit mmio: [0xf7f00000-0xf7ffffff]
Dec  6 15:14:50 weasel kernel: [    0.763401] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xcfd00000-0xcfdfffff]
Dec  6 15:14:50 weasel kernel: [    0.763440] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xcfc00000-0xcfcfffff]
Dec  6 15:14:50 weasel kernel: [    0.763479] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xcfe00000-0xcfefffff]
Dec  6 15:14:50 weasel kernel: [    0.763522] pci 0000:00:1e.0: transparent bridge
Dec  6 15:14:50 weasel kernel: [    0.763555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  6 15:14:50 weasel kernel: [    0.763701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Dec  6 15:14:50 weasel kernel: [    0.763755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
Dec  6 15:14:50 weasel kernel: [    0.763833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
Dec  6 15:14:50 weasel kernel: [    0.763885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR22._PRT]
Dec  6 15:14:50 weasel kernel: [    0.763930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR23._PRT]
Dec  6 15:14:50 weasel kernel: [    0.763974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
Dec  6 15:14:50 weasel kernel: [    0.768535] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
Dec  6 15:14:50 weasel kernel: [    0.768634] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Dec  6 15:14:50 weasel kernel: [    0.768732] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
Dec  6 15:14:50 weasel kernel: [    0.768830] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
Dec  6 15:14:50 weasel kernel: [    0.768928] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
Dec  6 15:14:50 weasel kernel: [    0.769027] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
Dec  6 15:14:50 weasel kernel: [    0.769126] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 6 7 10 11 12 14 15)
Dec  6 15:14:50 weasel kernel: [    0.769230] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
Dec  6 15:14:50 weasel kernel: [    0.769344] SCSI subsystem initialized
Dec  6 15:14:50 weasel kernel: [    0.769393] libata version 3.00 loaded.
Dec  6 15:14:50 weasel kernel: [    0.769434] usbcore: registered new interface driver usbfs
Dec  6 15:14:50 weasel kernel: [    0.769443] usbcore: registered new interface driver hub
Dec  6 15:14:50 weasel kernel: [    0.769459] usbcore: registered new device driver usb
Dec  6 15:14:50 weasel kernel: [    0.769535] ACPI: WMI: Mapper loaded
Dec  6 15:14:50 weasel kernel: [    0.769536] PCI: Using ACPI for IRQ routing
Dec  6 15:14:50 weasel kernel: [    0.797248] Bluetooth: Core ver 2.15
Dec  6 15:14:50 weasel kernel: [    0.797266] NET: Registered protocol family 31
Dec  6 15:14:50 weasel kernel: [    0.797268] Bluetooth: HCI device and connection manager initialized
Dec  6 15:14:50 weasel kernel: [    0.797269] Bluetooth: HCI socket layer initialized
Dec  6 15:14:50 weasel kernel: [    0.797271] NetLabel: Initializing
Dec  6 15:14:50 weasel kernel: [    0.797272] NetLabel:  domain hash size = 128
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Option
Dec  6 15:14:50 weasel kernel: [    0.797273] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  6 15:14:50 weasel kernel: [    0.797285] NetLabel:  unlabeled traffic allowed by default
Dec  6 15:14:50 weasel kernel: [    0.807225] Switched to high resolution mode on CPU 0
Dec  6 15:14:50 weasel kernel: [    0.808428] Switched to high resolution mode on CPU 3
Dec  6 15:14:50 weasel kernel: [    0.808436] Switched to high resolution mode on CPU 1
Dec  6 15:14:50 weasel kernel: [    0.808438] Switched to high resolution mode on CPU 2
Dec  6 15:14:50 weasel kernel: [    0.827176] pnp: PnP ACPI init
Dec  6 15:14:50 weasel kernel: [    0.827182] ACPI: bus type pnp registered
Dec  6 15:14:50 weasel kernel: [    0.829619] pnp: PnP ACPI: found 11 devices
Dec  6 15:14:50 weasel kernel: [    0.829620] ACPI: ACPI bus type pnp unregistered
Dec  6 15:14:50 weasel kernel: [    0.829627] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829629] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829631] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829633] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829638] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829640] system 00:06: ioport range 0x800-0x87f has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829642] system 00:06: ioport range 0x500-0x57f has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829644] system 00:06: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829646] system 00:06: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829648] system 00:06: iomem range 0xfed40000-0xfed8ffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829651] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec  6 15:14:50 weasel kernel: [    0.829653] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829656] system 00:08: ioport range 0x290-0x29f has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829659] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829663] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Dec  6 15:14:50 weasel kernel: [    0.829665] system 00:0a: iomem range 0xc0000-0xcffff has been reserved
Dec  6 15:14:50 weasel kernel: [    0.829667] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
Dec  6 15:14:50 weasel kernel: [    0.829668] system 00:0a: iomem range 0x100000-0xcbffffff could not be reserved
Dec  6 15:14:50 weasel kernel: [    0.829670] system 00:0a: iomem range 0xfed90000-0xffffffff could not be reserved
Dec  6 15:14:50 weasel kernel: [    0.834259] AppArmor: AppArmor Filesystem Enabled
Dec  6 15:14:50 weasel kernel: [    0.834308] pci 0000:00:03.0: PCI bridge, secondary bus 0000:07
Dec  6 15:14:50 weasel kernel: [    0.834311] pci 0000:00:03.0:   IO window: 0xe000-0xefff
Dec  6 15:14:50 weasel kernel: [    0.834314] pci 0000:00:03.0:   MEM window: 0xf8000000-0xfbffffff
Dec  6 15:14:50 weasel kernel: [    0.834317] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Dec  6 15:14:50 weasel kernel: [    0.834321] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
Dec  6 15:14:50 weasel kernel: [    0.834322] pci 0000:00:1c.0:   IO window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834325] pci 0000:00:1c.0:   MEM window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834328] pci 0000:00:1c.0:   PREFETCH window: 0x000000cff00000-0x000000cfffffff
Dec  6 15:14:50 weasel kernel: [    0.834333] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Dec  6 15:14:50 weasel kernel: [    0.834336] pci 0000:00:1c.1:   IO window: 0xc000-0xcfff
Dec  6 15:14:50 weasel kernel: [    0.834339] pci 0000:00:1c.1:   MEM window: 0xf7e00000-0xf7efffff
Dec  6 15:14:50 weasel kernel: [    0.834342] pci 0000:00:1c.1:   PREFETCH window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834345] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Dec  6 15:14:50 weasel kernel: [    0.834348] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
Dec  6 15:14:50 weasel kernel: [    0.834351] pci 0000:00:1c.2:   MEM window: 0xf7f00000-0xf7ffffff
Dec  6 15:14:50 weasel kernel: [    0.834355] pci 0000:00:1c.2:   PREFETCH window: 0x000000cfd00000-0x000000cfdfffff
Dec  6 15:14:50 weasel kernel: [    0.834359] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
Dec  6 15:14:50 weasel kernel: [    0.834361] pci 0000:00:1c.3:   IO window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834364] pci 0000:00:1c.3:   MEM window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834367] pci 0000:00:1c.3:   PREFETCH window: 0x000000cfc00000-0x000000cfcfffff
Dec  6 15:14:50 weasel kernel: [    0.834372] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Nokia
Dec  6 15:14:50 weasel kernel: [    0.834373] pci 0000:00:1c.4:   IO window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834376] pci 0000:00:1c.4:   MEM window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834379] pci 0000:00:1c.4:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff
Dec  6 15:14:50 weasel kernel: [    0.834384] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Dec  6 15:14:50 weasel kernel: [    0.834385] pci 0000:00:1e.0:   IO window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834389] pci 0000:00:1e.0:   MEM window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834392] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec  6 15:14:50 weasel kernel: [    0.834400]   alloc irq_desc for 16 on node 0
Dec  6 15:14:50 weasel kernel: [    0.834401]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.834405] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  6 15:14:50 weasel kernel: [    0.834408] pci 0000:00:03.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834413]   alloc irq_desc for 17 on node 0
Dec  6 15:14:50 weasel kernel: [    0.834414]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.834417] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  6 15:14:50 weasel kernel: [    0.834421] pci 0000:00:1c.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834426] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec  6 15:14:50 weasel kernel: [    0.834429] pci 0000:00:1c.1: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834434]   alloc irq_desc for 18 on node 0
Dec  6 15:14:50 weasel kernel: [    0.834435]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.834438] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  6 15:14:50 weasel kernel: [    0.834441] pci 0000:00:1c.2: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834446]   alloc irq_desc for 19 on node 0
Dec  6 15:14:50 weasel kernel: [    0.834447]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.834449] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec  6 15:14:50 weasel kernel: [    0.834453] pci 0000:00:1c.3: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834458] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  6 15:14:50 weasel kernel: [    0.834462] pci 0000:00:1c.4: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834467] pci 0000:00:1e.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.834470] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec  6 15:14:50 weasel kernel: [    0.834471] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Dec  6 15:14:50 weasel kernel: [    0.834473] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]
Dec  6 15:14:50 weasel kernel: [    0.834475] pci_bus 0000:07: resource 1 mem: [0xf8000000-0xfbffffff]
Dec  6 15:14:50 weasel kernel: [    0.834476] pci_bus 0000:07: resource 2 pref mem [0xd0000000-0xdfffffff]
Dec  6 15:14:50 weasel kernel: [    0.834478] pci_bus 0000:06: resource 2 pref mem [0xcff00000-0xcfffffff]
Dec  6 15:14:50 weasel kernel: [    0.834480] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
Dec  6 15:14:50 weasel kernel: [    0.834481] pci_bus 0000:02: resource 1 mem: [0xf7e00000-0xf7efffff]
Dec  6 15:14:50 weasel kernel: [    0.834483] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
Dec  6 15:14:50 weasel kernel: [    0.834485] pci_bus 0000:04: resource 1 mem: [0xf7f00000-0xf7ffffff]
Dec  6 15:14:50 weasel kernel: [    0.834486] pci_bus 0000:04: resource 2 pref mem [0xcfd00000-0xcfdfffff]
Dec  6 15:14:50 weasel kernel: [    0.834488] pci_bus 0000:03: resource 2 pref mem [0xcfc00000-0xcfcfffff]
Dec  6 15:14:50 weasel kernel: [    0.834490] pci_bus 0000:05: resource 2 pref mem [0xcfe00000-0xcfefffff]
Dec  6 15:14:50 weasel kernel: [    0.834491] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
Dec  6 15:14:50 weasel kernel: [    0.834493] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
Dec  6 15:14:50 weasel kernel: [    0.834513] NET: Registered protocol family 2
Dec  6 15:14:50 weasel kernel: [    0.834627] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  6 15:14:50 weasel kernel: [    0.835322] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec  6 15:14:50 weasel kernel: [    0.837625] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec  6 15:14:50 weasel kernel: [    0.837903] TCP: Hash tables configured (established 524288 bind 65536)
Dec  6 15:14:50 weasel kernel: [    0.837905] TCP reno registered
Dec  6 15:14:50 weasel kernel: [    0.837976] NET: Registered protocol family 1
Dec  6 15:14:50 weasel kernel: [    0.838017] Trying to unpack rootfs image as initramfs...
Dec  6 15:14:50 weasel kernel: [    0.974071] Freeing initrd memory: 7692k freed
Dec  6 15:14:50 weasel modem-manager: Loaded plugin Gobi
Dec  6 15:14:50 weasel kernel: [    0.975344] Scanning for low memory corruption every 60 seconds
Dec  6 15:14:50 weasel kernel: [    0.975428] audit: initializing netlink socket (disabled)
Dec  6 15:14:50 weasel kernel: [    0.975440] type=2000 audit(1260105279.830:1): initialized
Dec  6 15:14:50 weasel kernel: [    0.983303] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec  6 15:14:50 weasel kernel: [    0.984271] VFS: Disk quotas dquot_6.5.2
Dec  6 15:14:50 weasel kernel: [    0.984310] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec  6 15:14:50 weasel kernel: [    0.984726] fuse init (API version 7.12)
Dec  6 15:14:50 weasel kernel: [    0.984780] msgmni has been set to 6395
Dec  6 15:14:50 weasel kernel: [    0.984931] alg: No test for stdrng (krng)
Dec  6 15:14:50 weasel kernel: [    0.984938] io scheduler noop registered
Dec  6 15:14:50 weasel kernel: [    0.984939] io scheduler anticipatory registered
Dec  6 15:14:50 weasel kernel: [    0.984941] io scheduler deadline registered
Dec  6 15:14:50 weasel kernel: [    0.984969] io scheduler cfq registered (default)
Dec  6 15:14:50 weasel kernel: [    0.985026] pci 0000:07:00.0: Boot video device
Dec  6 15:14:50 weasel kernel: [    0.985126]   alloc irq_desc for 24 on node 0
Dec  6 15:14:50 weasel kernel: [    0.985128]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.985135] pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    0.985140] pcieport-driver 0000:00:03.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.985236]   alloc irq_desc for 25 on node 0
Dec  6 15:14:50 weasel kernel: [    0.985237]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.985243] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    0.985249] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.985413]   alloc irq_desc for 26 on node 0
Dec  6 15:14:50 weasel kernel: [    0.985414]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.985420] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    0.985426] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.985517]   alloc irq_desc for 27 on node 0
Dec  6 15:14:50 weasel kernel: [    0.985519]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.985524] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    0.985530] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.985623]   alloc irq_desc for 28 on node 0
Dec  6 15:14:50 weasel kernel: [    0.985624]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.985630] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    0.985636] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.985730]   alloc irq_desc for 29 on node 0
Dec  6 15:14:50 weasel kernel: [    0.985732]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    0.985737] pcieport-driver 0000:00:1c.4: irq 29 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    0.985744] pcieport-driver 0000:00:1c.4: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.985808] Firmware did not grant requested _OSC control
Dec  6 15:14:50 weasel kernel: [    0.985810] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
Dec  6 15:14:50 weasel kernel: [    0.985817] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  6 15:14:50 weasel kernel: [    0.985826] Firmware did not grant requested _OSC control
Dec  6 15:14:50 weasel kernel: [    0.985838] Firmware did not grant requested _OSC control
Dec  6 15:14:50 weasel kernel: [    0.985856] Firmware did not grant requested _OSC control
Dec  6 15:14:50 weasel kernel: [    0.985865] Firmware did not grant requested _OSC control
Dec  6 15:14:50 weasel kernel: [    0.985875] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec  6 15:14:50 weasel kernel: [    0.985946] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec  6 15:14:50 weasel kernel: [    0.985948] ACPI: Power Button [PWRF]
Dec  6 15:14:50 weasel kernel: [    0.985985] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Dec  6 15:14:50 weasel kernel: [    0.985987] ACPI: Power Button [PWRB]
Dec  6 15:14:50 weasel kernel: [    0.986790] ACPI: SSDT 00000000cb7821e0 01130 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
Dec  6 15:14:50 weasel kernel: [    0.987124] ACPI: SSDT 00000000cb783310 004D5 (v01  PmRef  P001Cst 00003001 INTL 20051117)
Dec  6 15:14:50 weasel kernel: [    0.987417] Monitor-Mwait will be used to enter C-1 state
Dec  6 15:14:50 weasel kernel: [    0.987433] Monitor-Mwait will be used to enter C-2 state
Dec  6 15:14:50 weasel kernel: [    0.987445] Monitor-Mwait will be used to enter C-3 state
Dec  6 15:14:50 weasel kernel: [    0.987461] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec  6 15:14:50 weasel kernel: [    0.987476] processor LNXCPU:00: registered as cooling_device0
Dec  6 15:14:50 weasel kernel: [    0.987648] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec  6 15:14:50 weasel kernel: [    0.987661] processor LNXCPU:01: registered as cooling_device1
Dec  6 15:14:50 weasel kernel: [    0.987835] ACPI: CPU2 (power states: C1[C1] C2[C2] C3[C3])
Dec  6 15:14:50 weasel kernel: [    0.987846] processor LNXCPU:02: registered as cooling_device2
Dec  6 15:14:50 weasel kernel: [    0.988019] ACPI: CPU3 (power states: C1[C1] C2[C2] C3[C3])
Dec  6 15:14:50 weasel kernel: [    0.988030] processor LNXCPU:03: registered as cooling_device3
Dec  6 15:14:50 weasel kernel: [    0.991027] Linux agpgart interface v0.103
Dec  6 15:14:50 weasel kernel: [    0.991033] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec  6 15:14:50 weasel kernel: [    0.991778] brd: module loaded
Dec  6 15:14:50 weasel kernel: [    0.992046] loop: module loaded
Dec  6 15:14:50 weasel kernel: [    0.992088] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec  6 15:14:50 weasel kernel: [    0.992175] ata_piix 0000:00:1f.2: version 2.13
Dec  6 15:14:50 weasel kernel: [    0.992185] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec  6 15:14:50 weasel kernel: [    0.992188] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Dec  6 15:14:50 weasel kernel: [    0.992214] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.992261] scsi0 : ata_piix
Dec  6 15:14:50 weasel kernel: [    0.992308] scsi1 : ata_piix
Dec  6 15:14:50 weasel kernel: [    0.993366] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
Dec  6 15:14:50 weasel kernel: [    0.993371] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
Dec  6 15:14:50 weasel kernel: [    0.993404] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec  6 15:14:50 weasel kernel: [    0.993408] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Dec  6 15:14:50 weasel kernel: [    0.993429] ata_piix 0000:00:1f.5: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.993464] scsi2 : ata_piix
Dec  6 15:14:50 weasel kernel: [    0.993496] scsi3 : ata_piix
Dec  6 15:14:50 weasel kernel: [    0.994372] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
Dec  6 15:14:50 weasel kernel: [    0.994375] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
Dec  6 15:14:50 weasel kernel: [    0.994676] pata_via 0000:02:00.1: version 0.3.4
Dec  6 15:14:50 weasel kernel: [    0.994685] pata_via 0000:02:00.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  6 15:14:50 weasel kernel: [    0.994731] pata_via 0000:02:00.1: PCI INT A disabled
Dec  6 15:14:50 weasel kernel: [    0.994790] pata_acpi 0000:02:00.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  6 15:14:50 weasel kernel: [    0.994808] pata_acpi 0000:02:00.1: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.994818] pata_acpi 0000:02:00.1: PCI INT A disabled
Dec  6 15:14:50 weasel kernel: [    0.995006] Fixed MDIO Bus: probed
Dec  6 15:14:50 weasel kernel: [    0.995025] PPP generic driver version 2.4.2
Dec  6 15:14:50 weasel kernel: [    0.995079] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec  6 15:14:50 weasel kernel: [    0.995104] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  6 15:14:50 weasel kernel: [    0.995112] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    0.995114] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Dec  6 15:14:50 weasel kernel: [    0.995146] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec  6 15:14:50 weasel kernel: [    0.999051] ehci_hcd 0000:00:1a.0: debug port 2
Dec  6 15:14:50 weasel kernel: [    0.999056] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
Dec  6 15:14:50 weasel kernel: [    0.999065] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7df6000
Dec  6 15:14:50 weasel kernel: [    1.016717] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Dec  6 15:14:50 weasel kernel: [    1.016781] usb usb1: configuration #1 chosen from 1 choice
Dec  6 15:14:50 weasel kernel: [    1.016802] hub 1-0:1.0: USB hub found
Dec  6 15:14:50 weasel kernel: [    1.016806] hub 1-0:1.0: 6 ports detected
Dec  6 15:14:50 weasel kernel: [    1.016924]   alloc irq_desc for 23 on node 0
Dec  6 15:14:50 weasel kernel: [    1.016926]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    1.016930] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  6 15:14:50 weasel kernel: [    1.016937] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    1.016940] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Dec  6 15:14:50 weasel kernel: [    1.016961] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec  6 15:14:50 weasel kernel: [    1.020899] ehci_hcd 0000:00:1d.0: debug port 2
Dec  6 15:14:50 weasel kernel: [    1.020904] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
Dec  6 15:14:50 weasel kernel: [    1.020913] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7dfc000
Dec  6 15:14:50 weasel kernel: [    1.036657] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Dec  6 15:14:50 weasel kernel: [    1.036695] usb usb2: configuration #1 chosen from 1 choice
Dec  6 15:14:50 weasel kernel: [    1.036711] hub 2-0:1.0: USB hub found
Dec  6 15:14:50 weasel kernel: [    1.036714] hub 2-0:1.0: 8 ports detected
Dec  6 15:14:50 weasel kernel: [    1.036764] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  6 15:14:50 weasel kernel: [    1.036774] uhci_hcd: USB Universal Host Controller Interface driver
Dec  6 15:14:50 weasel kernel: [    1.036832] PNP: No PS/2 controller found. Probing ports directly.
Dec  6 15:14:50 weasel kernel: [    1.039259] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  6 15:14:50 weasel kernel: [    1.039267] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec  6 15:14:50 weasel kernel: [    1.039313] mice: PS/2 mouse device common for all mice
Dec  6 15:14:50 weasel kernel: [    1.039365] rtc_cmos 00:03: RTC can wake from S4
Dec  6 15:14:50 weasel kernel: [    1.039386] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec  6 15:14:50 weasel kernel: [    1.039408] rtc0: alarms up to one month, y3k, 114 bytes nvram
Dec  6 15:14:50 weasel kernel: [    1.039475] device-mapper: uevent: version 1.0.3
Dec  6 15:14:50 weasel kernel: [    1.039525] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec  6 15:14:50 weasel kernel: [    1.039578] device-mapper: multipath: version 1.1.0 loaded
Dec  6 15:14:50 weasel kernel: [    1.039580] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec  6 15:14:50 weasel kernel: [    1.039772] cpuidle: using governor ladder
Dec  6 15:14:50 weasel kernel: [    1.039894] cpuidle: using governor menu
Dec  6 15:14:50 weasel kernel: [    1.040173] TCP cubic registered
Dec  6 15:14:50 weasel kernel: [    1.040257] NET: Registered protocol family 10
Dec  6 15:14:50 weasel kernel: [    1.040564] lo: Disabled Privacy Extensions
Dec  6 15:14:50 weasel kernel: [    1.040760] NET: Registered protocol family 17
Dec  6 15:14:50 weasel kernel: [    1.040770] Bluetooth: L2CAP ver 2.13
Dec  6 15:14:50 weasel kernel: [    1.040771] Bluetooth: L2CAP socket layer initialized
Dec  6 15:14:50 weasel kernel: [    1.040773] Bluetooth: SCO (Voice Link) ver 0.6
Dec  6 15:14:50 weasel kernel: [    1.040774] Bluetooth: SCO socket layer initialized
Dec  6 15:14:50 weasel kernel: [    1.040787] Bluetooth: RFCOMM TTY layer initialized
Dec  6 15:14:50 weasel kernel: [    1.040789] Bluetooth: RFCOMM socket layer initialized
Dec  6 15:14:50 weasel kernel: [    1.040790] Bluetooth: RFCOMM ver 1.11
Dec  6 15:14:50 weasel kernel: [    1.041892] PM: Resume from disk failed.
Dec  6 15:14:50 weasel kernel: [    1.041898] registered taskstats version 1
Dec  6 15:14:50 weasel kernel: [    1.041982]   Magic number: 5:34:230
Dec  6 15:14:50 weasel kernel: [    1.042135] rtc_cmos 00:03: setting system clock to 2009-12-06 13:14:40 UTC (1260105280)
Dec  6 15:14:50 weasel kernel: [    1.042139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  6 15:14:50 weasel kernel: [    1.042142] EDD information not available.
Dec  6 15:14:50 weasel kernel: [    1.336061] usb 1-1: new high speed USB device using ehci_hcd and address 2
Dec  6 15:14:50 weasel kernel: [    1.346923] ata3: SATA link down (SStatus 0 SControl 300)
Dec  6 15:14:50 weasel kernel: [    1.357762] ata4: SATA link down (SStatus 0 SControl 300)
Dec  6 15:14:50 weasel kernel: [    1.486176] usb 1-1: configuration #1 chosen from 1 choice
Dec  6 15:14:50 weasel kernel: [    1.486396] hub 1-1:1.0: USB hub found
Dec  6 15:14:50 weasel kernel: [    1.486600] hub 1-1:1.0: 6 ports detected
Dec  6 15:14:50 weasel kernel: [    1.605396] usb 2-1: new high speed USB device using ehci_hcd and address 2
Dec  6 15:14:50 weasel kernel: [    1.756101] usb 2-1: configuration #1 chosen from 1 choice
Dec  6 15:14:50 weasel kernel: [    1.756322] hub 2-1:1.0: USB hub found
Dec  6 15:14:50 weasel kernel: [    1.756527] hub 2-1:1.0: 8 ports detected
Dec  6 15:14:50 weasel kernel: [    1.844850] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  6 15:14:50 weasel kernel: [    1.844864] ata1.01: SATA link down (SStatus 0 SControl 300)
Dec  6 15:14:50 weasel kernel: [    1.845037] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec  6 15:14:50 weasel kernel: [    1.845049] ata2.01: SATA link down (SStatus 0 SControl 300)
Dec  6 15:14:50 weasel kernel: [    1.845058] ata2.01: link offline, clearing class 3 to NONE
Dec  6 15:14:50 weasel kernel: [    1.865776] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL00, max UDMA/100
Dec  6 15:14:50 weasel kernel: [    1.866556] ata1.00: ATA-8: WDC WD2500AAKS-00L9A0, 01.03E01, max UDMA/133
Dec  6 15:14:50 weasel kernel: [    1.866562] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  6 15:14:50 weasel kernel: [    1.887510] ata1.00: configured for UDMA/133
Dec  6 15:14:50 weasel kernel: [    1.887762] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
Dec  6 15:14:50 weasel kernel: [    1.887828] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  6 15:14:50 weasel kernel: [    1.887848] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Dec  6 15:14:50 weasel kernel: [    1.887869] sd 0:0:0:0: [sda] Write Protect is off
Dec  6 15:14:50 weasel kernel: [    1.887870] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec  6 15:14:50 weasel kernel: [    1.887882] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  6 15:14:50 weasel kernel: [    1.887944]  sda: sda1 sda2 <
Dec  6 15:14:50 weasel kernel: [    1.904862] ata2.00: configured for UDMA/100
Dec  6 15:14:50 weasel kernel: [    1.911725] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL00 PQ: 0 ANSI: 5
Dec  6 15:14:50 weasel kernel: [    1.923605]  sda5 >
Dec  6 15:14:50 weasel kernel: [    1.923892] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  6 15:14:50 weasel kernel: [    1.925985] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec  6 15:14:50 weasel kernel: [    1.925991] Uniform CD-ROM driver Revision: 3.20
Dec  6 15:14:50 weasel kernel: [    1.926095] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec  6 15:14:50 weasel kernel: [    1.926142] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec  6 15:14:50 weasel kernel: [    1.926286] Freeing unused kernel memory: 660k freed
Dec  6 15:14:50 weasel kernel: [    1.926381] Write protecting the kernel read-only data: 7584k
Dec  6 15:14:50 weasel kernel: [    1.988131] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec  6 15:14:50 weasel kernel: [    1.988147] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  6 15:14:50 weasel kernel: [    1.988177] r8169 0000:04:00.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    1.988216]   alloc irq_desc for 30 on node 0
Dec  6 15:14:50 weasel kernel: [    1.988217]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    1.988229] r8169 0000:04:00.0: irq 30 for MSI/MSI-X
Dec  6 15:14:50 weasel kernel: [    1.988589] eth0: RTL8168d/8111d at 0xffffc90000620000, 00:19:66:f1:17:12, XID 281000c0 IRQ 30
Dec  6 15:14:50 weasel kernel: [    2.004739] ohci1394 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  6 15:14:50 weasel kernel: [    2.004745] ohci1394 0000:02:00.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [    2.045044] usb 2-1.5: new low speed USB device using ehci_hcd and address 3
Dec  6 15:14:50 weasel kernel: [    2.066318] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f7eef800-f7eeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec  6 15:14:50 weasel kernel: [    2.180270] usb 2-1.5: configuration #1 chosen from 1 choice
Dec  6 15:14:50 weasel kernel: [    2.184677] usbcore: registered new interface driver hiddev
Dec  6 15:14:50 weasel kernel: [    2.194450] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3
Dec  6 15:14:50 weasel kernel: [    2.194492] generic-usb 0003:046D:C30E.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:1d.0-1.5/input0
Dec  6 15:14:50 weasel kernel: [    2.214951] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input4
Dec  6 15:14:50 weasel kernel: [    2.215034] generic-usb 0003:046D:C30E.0002: input,hidraw1: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:1d.0-1.5/input1
Dec  6 15:14:50 weasel kernel: [    2.215057] usbcore: registered new interface driver usbhid
Dec  6 15:14:50 weasel kernel: [    2.215062] usbhid: v2.6:USB HID core driver
Dec  6 15:14:50 weasel kernel: [    2.264430] usb 2-1.6: new low speed USB device using ehci_hcd and address 4
Dec  6 15:14:50 weasel kernel: [    2.379315] usb 2-1.6: configuration #1 chosen from 1 choice
Dec  6 15:14:50 weasel kernel: [    2.381998] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
Dec  6 15:14:50 weasel kernel: [    2.382032] generic-usb 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.6/input0
Dec  6 15:14:50 weasel kernel: [    3.104447] PM: Starting manual resume from disk
Dec  6 15:14:50 weasel kernel: [    3.104449] PM: Resume from partition 8:5
Dec  6 15:14:50 weasel kernel: [    3.104450] PM: Checking hibernation image.
Dec  6 15:14:50 weasel kernel: [    3.104647] PM: Resume from disk failed.
Dec  6 15:14:50 weasel kernel: [    3.137322] EXT4-fs (sda1): barriers enabled
Dec  6 15:14:50 weasel kernel: [    3.161539] kjournald2 starting: pid 434, dev sda1:8, commit interval 5 seconds
Dec  6 15:14:50 weasel kernel: [    3.161565] EXT4-fs (sda1): delayed allocation enabled
Dec  6 15:14:50 weasel kernel: [    3.161568] EXT4-fs: file extents enabled
Dec  6 15:14:50 weasel kernel: [    3.171269] EXT4-fs: mballoc enabled
Dec  6 15:14:50 weasel kernel: [    3.171276] EXT4-fs (sda1): mounted filesystem with ordered data mode
Dec  6 15:14:50 weasel kernel: [    3.392298] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[008f1300374a0600]
Dec  6 15:14:50 weasel kernel: [    3.628664] type=1505 audit(1260105283.086:2): operation="profile_load" pid=457 name=/usr/share/gdm/guest-session/Xsession
Dec  6 15:14:50 weasel kernel: [    3.630502] type=1505 audit(1260105283.086:3): operation="profile_load" pid=458 name=/sbin/dhclient3
Dec  6 15:14:50 weasel kernel: [    3.630836] type=1505 audit(1260105283.086:4): operation="profile_load" pid=458 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec  6 15:14:50 weasel kernel: [    3.631063] type=1505 audit(1260105283.086:5): operation="profile_load" pid=458 name=/usr/lib/connman/scripts/dhclient-script
Dec  6 15:14:50 weasel kernel: [    3.672283] type=1505 audit(1260105283.134:6): operation="profile_load" pid=459 name=/usr/bin/evince
Dec  6 15:14:50 weasel kernel: [    3.677637] type=1505 audit(1260105283.134:7): operation="profile_load" pid=459 name=/usr/bin/evince-previewer
Dec  6 15:14:50 weasel kernel: [    3.680969] type=1505 audit(1260105283.144:8): operation="profile_load" pid=459 name=/usr/bin/evince-thumbnailer
Dec  6 15:14:50 weasel kernel: [    3.701970] type=1505 audit(1260105283.156:9): operation="profile_load" pid=461 name=/usr/lib/cups/backend/cups-pdf
Dec  6 15:14:50 weasel kernel: [    3.702366] type=1505 audit(1260105283.166:10): operation="profile_load" pid=461 name=/usr/sbin/cupsd
Dec  6 15:14:50 weasel kernel: [    9.784683] udev: starting version 147
Dec  6 15:14:50 weasel kernel: [    9.811387] lp: driver loaded but no devices found
Dec  6 15:14:50 weasel kernel: [    9.824290] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec  6 15:14:50 weasel kernel: [    9.825917] Adding 9598796k swap on /dev/sda5.  Priority:-1 extents:1 across:9598796k 
Dec  6 15:14:50 weasel kernel: [    9.841586] nvidia: module license 'NVIDIA' taints kernel.
Dec  6 15:14:50 weasel kernel: [    9.841588] Disabling lock debugging due to kernel taint
Dec  6 15:14:50 weasel kernel: [    9.878343]   alloc irq_desc for 22 on node 0
Dec  6 15:14:50 weasel kernel: [    9.878345]   alloc kstat_irqs on node 0
Dec  6 15:14:50 weasel kernel: [    9.878350] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec  6 15:14:50 weasel kernel: [    9.878374] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [   10.093526] nvidia 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  6 15:14:50 weasel kernel: [   10.093538] nvidia 0000:07:00.0: setting latency timer to 64
Dec  6 15:14:50 weasel kernel: [   10.093662] EXT4-fs (sda1): internal journal on sda1:8
Dec  6 15:14:50 weasel kernel: [   10.093683] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Dec  6 15:14:50 weasel kernel: [   10.456071] __ratelimit: 6 callbacks suppressed
Dec  6 15:14:50 weasel kernel: [   10.456073] type=1505 audit(1260105289.936:13): operation="profile_replace" pid=926 name=/usr/share/gdm/guest-session/Xsession
Dec  6 15:14:50 weasel kernel: [   10.457334] type=1505 audit(1260105289.936:14): operation="profile_replace" pid=927 name=/sbin/dhclient3
Dec  6 15:14:50 weasel kernel: [   10.457669] type=1505 audit(1260105289.936:15): operation="profile_replace" pid=927 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec  6 15:14:50 weasel kernel: [   10.457853] type=1505 audit(1260105289.936:16): operation="profile_replace" pid=927 name=/usr/lib/connman/scripts/dhclient-script
Dec  6 15:14:50 weasel kernel: [   10.459695] type=1505 audit(1260105289.936:17): operation="profile_replace" pid=928 name=/usr/bin/evince
Dec  6 15:14:50 weasel kernel: [   10.465140] type=1505 audit(1260105289.936:18): operation="profile_replace" pid=928 name=/usr/bin/evince-previewer
Dec  6 15:14:50 weasel kernel: [   10.468365] type=1505 audit(1260105289.946:19): operation="profile_replace" pid=928 name=/usr/bin/evince-thumbnailer
Dec  6 15:14:50 weasel kernel: [   10.473311] type=1505 audit(1260105289.946:20): operation="profile_replace" pid=930 name=/usr/lib/cups/backend/cups-pdf
Dec  6 15:14:50 weasel kernel: [   10.473719] type=1505 audit(1260105289.946:21): operation="profile_replace" pid=930 name=/usr/sbin/cupsd
Dec  6 15:14:50 weasel kernel: [   10.475061] type=1505 audit(1260105289.946:22): operation="profile_replace" pid=931 name=/usr/sbin/mysqld-akonadi
Dec  6 15:14:49 weasel rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec  6 15:14:50 weasel avahi-daemon[829]: Successfully called chroot().
Dec  6 15:14:50 weasel avahi-daemon[829]: Successfully dropped remaining capabilities.
Dec  6 15:14:50 weasel NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec  6 15:14:50 weasel NetworkManager: <info>  Wireless now enabled by radio killswitch
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: (14471264) ... get_connections.
Dec  6 15:14:50 weasel NetworkManager:    SCPlugin-Ifupdown: (14471264) ... get_connections (managed=false): return empty list.
Dec  6 15:14:50 weasel NetworkManager:    Ifupdown: get unmanaged devices count: 0
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): carrier is OFF
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): now managed
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): bringing up device.
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): preparing device.
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Dec  6 15:14:50 weasel NetworkManager: <info>  modem-manager is now available
Dec  6 15:14:50 weasel NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec  6 15:14:50 weasel NetworkManager: <info>  Trying to start the supplicant...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  6 15:14:50 weasel NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec  6 15:14:50 weasel NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec  6 15:14:50 weasel kernel: [   10.548962] r8169: eth0: link up
Dec  6 15:14:50 weasel kernel: [   10.548966] r8169: eth0: link up
Dec  6 15:14:50 weasel avahi-daemon[829]: No service file found in /etc/avahi/services.
Dec  6 15:14:50 weasel avahi-daemon[829]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.42.
Dec  6 15:14:50 weasel avahi-daemon[829]: New relevant interface eth0.IPv4 for mDNS.
Dec  6 15:14:50 weasel avahi-daemon[829]: Network interface enumeration completed.
Dec  6 15:14:50 weasel avahi-daemon[829]: Registering new address record for fe80::219:66ff:fef1:1712 on eth0.*.
Dec  6 15:14:50 weasel avahi-daemon[829]: Registering new address record for 192.168.1.42 on eth0.IPv4.
Dec  6 15:14:50 weasel avahi-daemon[829]: Registering HINFO record with values 'X86_64'/'LINUX'.
Dec  6 15:14:50 weasel init: apport pre-start process (1095) terminated with status 1
Dec  6 15:14:50 weasel cron[1099]: (CRON) INFO (pidfile fd = 3)
Dec  6 15:14:50 weasel anacron[1122]: Anacron 2.3 started on 2009-12-06
Dec  6 15:14:50 weasel init: apport post-stop process (1106) terminated with status 1
Dec  6 15:14:50 weasel cron[1125]: (CRON) STARTUP (fork ok)
Dec  6 15:14:50 weasel cron[1125]: (CRON) INFO (Running @reboot jobs)
Dec  6 15:14:50 weasel anacron[1122]: Will run job `cron.weekly' in 10 min.
Dec  6 15:14:50 weasel anacron[1122]: Jobs will be executed sequentially
Dec  6 15:14:50 weasel kernel: [   11.003332] ppdev: user-space parallel port driver
Dec  6 15:14:50 weasel gdm-binary[1075]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Dec  6 15:14:50 weasel kernel: [   11.215370] usplash:397 freeing invalid memtype fffffffff9000000-fffffffff9e00000
Dec  6 15:14:50 weasel gdm-simple-slave[1366]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Dec  6 15:14:50 weasel gdm-binary[1075]: WARNING: Unable to find users: no seat-id found
Dec  6 15:14:50 weasel acpid: client connected from 1370[0:0]
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb1
Dec  6 15:14:50 weasel udev-configure-printer: Failed to get parent
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb1
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 1D6B:0002
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb1/1-1
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0
Dec  6 15:14:50 weasel udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
Dec  6 15:14:50 weasel init: anacron main process (1122) killed by TERM signal
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb1
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 1D6B:0002
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 046D:C30E
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 1D6B:0002
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: Failed to get parent
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 046D:C30E
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 8087:0020
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 8087:0020
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 8087:0020
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb1/1-1
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 8087:0020
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 1D6B:0002
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6
Dec  6 15:14:50 weasel udev-configure-printer: Device vendor/product is 045E:0040
Dec  6 15:14:50 weasel udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  6 15:14:50 weasel avahi-daemon[829]: Server startup complete. Host name is weasel.local. Local service cookie is 2727599114.
Dec  6 15:14:51 weasel NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Dec  6 15:14:51 weasel NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec  6 15:14:51 weasel NetworkManager: <info>  Activation (eth0) successful, device activated.
Dec  6 15:14:51 weasel NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec  6 15:14:51 weasel ntpdate[1544]: adjust time server 91.189.94.4 offset 0.120996 sec
Dec  6 15:14:55 weasel acpid: client connected from 1020[107:114]
Dec  6 15:14:56 weasel kernel: [   11.414969] CPU0 attaching NULL sched-domain.
Dec  6 15:14:56 weasel kernel: [   11.414972] CPU1 attaching NULL sched-domain.
Dec  6 15:14:56 weasel kernel: [   11.414974] CPU2 attaching NULL sched-domain.
Dec  6 15:14:56 weasel kernel: [   11.414975] CPU3 attaching NULL sched-domain.
Dec  6 15:14:56 weasel kernel: [   11.472208] CPU0 attaching sched-domain:
Dec  6 15:14:56 weasel kernel: [   11.472210]  domain 0: span 0-3 level MC
Dec  6 15:14:56 weasel kernel: [   11.472211]   groups: 0 1 2 3
Dec  6 15:14:56 weasel kernel: [   11.472213]   domain 1: span 0-3 level CPU
Dec  6 15:14:56 weasel kernel: [   11.472214]    groups: 0-3 (__cpu_power = 4096)
Dec  6 15:14:56 weasel kernel: [   11.472217] CPU1 attaching sched-domain:
Dec  6 15:14:56 weasel kernel: [   11.472218]  domain 0: span 0-3 level MC
Dec  6 15:14:56 weasel kernel: [   11.472219]   groups: 1 2 3 0
Dec  6 15:14:56 weasel kernel: [   11.472221]   domain 1: span 0-3 level CPU
Dec  6 15:14:56 weasel kernel: [   11.472222]    groups: 0-3 (__cpu_power = 4096)
Dec  6 15:14:56 weasel kernel: [   11.472224] CPU2 attaching sched-domain:
Dec  6 15:14:56 weasel kernel: [   11.472224]  domain 0: span 0-3 level MC
Dec  6 15:14:56 weasel kernel: [   11.472225]   groups: 2 3 0 1
Dec  6 15:14:56 weasel kernel: [   11.472227]   domain 1: span 0-3 level CPU
Dec  6 15:14:56 weasel kernel: [   11.472228]    groups: 0-3 (__cpu_power = 4096)
Dec  6 15:14:56 weasel kernel: [   11.472230] CPU3 attaching sched-domain:
Dec  6 15:14:56 weasel kernel: [   11.472231]  domain 0: span 0-3 level MC
Dec  6 15:14:56 weasel kernel: [   11.472231]   groups: 3 0 1 2
Dec  6 15:14:56 weasel kernel: [   11.472233]   domain 1: span 0-3 level CPU
Dec  6 15:14:56 weasel kernel: [   11.472234]    groups: 0-3 (__cpu_power = 4096)
Dec  6 15:14:56 weasel acpid: client connected from 1370[0:0]
Dec  6 15:14:57 weasel console-kit-daemon[832]: WARNING: Couldn't read /proc/828/environ: Failed to open file '/proc/828/environ': No such file or directory
Dec  6 15:14:57 weasel anacron[1656]: Anacron 2.3 started on 2009-12-06
Dec  6 15:14:57 weasel anacron[1656]: Will run job `cron.weekly' in 10 min.
Dec  6 15:14:57 weasel anacron[1656]: Jobs will be executed sequentially
Dec  6 15:14:57 weasel kernel: [   18.186769] CPU0 attaching NULL sched-domain.
Dec  6 15:14:57 weasel kernel: [   18.186773] CPU1 attaching NULL sched-domain.
Dec  6 15:14:57 weasel kernel: [   18.186774] CPU2 attaching NULL sched-domain.
Dec  6 15:14:57 weasel kernel: [   18.186775] CPU3 attaching NULL sched-domain.
Dec  6 15:14:57 weasel kernel: [   18.231130] CPU0 attaching sched-domain:
Dec  6 15:14:57 weasel kernel: [   18.231133]  domain 0: span 0-3 level MC
Dec  6 15:14:57 weasel kernel: [   18.231134]   groups: 0 1 2 3
Dec  6 15:14:57 weasel kernel: [   18.231144] CPU1 attaching sched-domain:
Dec  6 15:14:57 weasel kernel: [   18.231145]  domain 0: span 0-3 level MC
Dec  6 15:14:57 weasel kernel: [   18.231146]   groups: 1 2 3 0
Dec  6 15:14:57 weasel kernel: [   18.231149] CPU2 attaching sched-domain:
Dec  6 15:14:57 weasel kernel: [   18.231150]  domain 0: span 0-3 level MC
Dec  6 15:14:57 weasel kernel: [   18.231151]   groups: 2 3 0 1
Dec  6 15:14:57 weasel kernel: [   18.231153] CPU3 attaching sched-domain:
Dec  6 15:14:57 weasel kernel: [   18.231154]  domain 0: span 0-3 level MC
Dec  6 15:14:57 weasel kernel: [   18.231155]   groups: 3 0 1 2
```

As I understand, the fix had to be in the kernel from today ... or ? It seams that it is not (I waited for a fix and didn't try the suggested pre-build because of the problems that where nvidia driver I happen to have :) too )

Can anyone tell me what to do ... I am total newby ... so please excuse me if I can't say the 'right' think. I need however my old Maxtor drive. I expected a patch/reboot should do the trick. Did I missed something ?

thanks !!!

ps. I have tried a Knoppix 6.2 live cd today and my hdd has been detected/accessed without any trouble.

---

### Post by goremache on 2009-12-13
I made an update today and it's working :) 

thanks for support

---

### Post by PatrickD-52761 on 2009-12-13
I too, am having this problem.  The drive in question is a Matshita UJ841S DVD RAM drive in my Toshiba Satellite A105-S2194 laptop.  It worked up until a couple of weeks ago.  On Windows, I would occasionally get a BSOD (which may or may not be related to the drive) and when I tried booting into Kubuntu, it would lock up during boot at the "Starting up...." screen.
 
I tried booting into Recovery mode, and after a few failed attempts each time, I would get in.  I would see a combination of messages about ata4: failing (Lost Interrupt 0x50 and Lost Interrupt 0x51) or that it was trying to configure it with UMA/33 and then UMA/25 (and something like DVD_DRY errors).
 
I was assuming that it was the drive failing, so I came here to find out how to disable it completely.  But with this thread, I think I found the answer.  Now it's a matter of getting the updates to work.
 
Have a great day:)
Patrick.

---

