---
title: "No sound on EeePC 1101HA"
date: 2010-02-28
forum: Hardware
---

### Post by NCLI on 2010-02-28
The only Output shown under Hardware Output is "Dummy Output." I simply can't figure out how to make it work. Here's lshw:
```
    description: Notebook
    product: 1101HA
    vendor: ASUSTeK Computer INC.
    version: x.x
    serial: A1OAAS015167
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=80C62B3A-F862-4681-38D8-E0CB4E5D9BFC
  *-core
       description: Motherboard
       product: 1101HA
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.xx
       serial: EeePC-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0322 (11/05/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1333MHz
          capacity: 1333MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 xtpr pdcm movbe lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank
             description: SODIMM DDR2 Synchronous
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: System Controller Hub (SCH Poulsbo)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: System Controller Hub (SCH Poulsbo) Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list rom
             configuration: driver=psb latency=0
             resources: irq:22 memory:f3f80000-f3ffffff ioport:c880(size=8) memory:d0000000-dfffffff memory:f3f40000-f3f7ffff
        *-multimedia UNCLAIMED
             description: Audio device
             product: System Controller Hub (SCH Poulsbo) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:f3f38000-f3f3bfff
        *-pci:0
             description: PCI bridge
             product: System Controller Hub (SCH Poulsbo) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:16 ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-network
                description: Ethernet interface
                product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: c0
                serial: e0:cb:4e:5d:9b:fc
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:24 memory:fbfc0000-fbffffff ioport:e880(size=128)
        *-pci:1
             description: PCI bridge
             product: System Controller Hub (SCH Poulsbo) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:17 ioport:d000(size=4096) memory:f4000000-fbefffff memory:cc000000-cfffffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:25:d3:e8:d2:8e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.111 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:fbef0000-fbefffff
        *-usb:0
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:b880(size=32)
        *-usb:1
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c080(size=32)
        *-usb:2
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c480(size=32)
        *-usb:3
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f3f37c00-f3f37fff
        *-isa
             description: ISA bridge
             product: System Controller Hub (SCH Poulsbo) LPC Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: isa
             configuration: latency=0
        *-ide
             description: IDE interface
             product: System Controller Hub (SCH Poulsbo) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sch latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: Hitachi HTS54502
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PB2O
                serial: 091109PB42061SCPGS9L
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=55121856
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7dd178f6-59ca-472c-bd93-3002bfa15bba
                   size: 227GiB
                   capacity: 227GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-27 04:44:39 filesystem=ext4 lastmountpoint=/V&#65533;&#960;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;ê&#65533;x^&#65533;&#65533;\&#65533;&#65533;Y&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;^&#65533;&#65533;^&#65533;&#65533;e^&#65533;&#65533;p&#65533;&#65533;p&#65533;%&#65533;r modified=2010-02-28 18:58:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-02-28 19:05:57 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5867MiB
                   capacity: 5867MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5867MiB
                      capabilities: nofs

```

---

### Post by NCLI on 2010-03-04
Gonna bump this.

---

