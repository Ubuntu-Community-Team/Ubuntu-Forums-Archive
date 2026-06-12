---
title: "CDROM Not Recognized"
date: 2014-09-01
forum: Hardware
---

### Post by egillen84 on 2014-09-01
I just installed Ubuntu 14.04 onto my new laptop. Most things are working great but my optical drive does not open when I press the button. When I investigated why, I found that there is no 'cdrom' device in my system. I cannot figure out how to get my optical drive detected, mounted, and working. Just a note: lshw -C cdrom comes up with nothing. Does anyone know what to do?


Here is the output of lshw:

```
description: Notebook
    product: Aspire V3-472P (Aspire V3-472P_0879_1_01)
    vendor: Acer
    version: TBD by OEM
    serial: NXMMZAA0014261F4217600
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 ldt16 vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=Type1Family frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=Aspire V3-472P_0879_1_01 uuid=60FC8FA9-F861-4EEC-9B34-DC81E4083389
  *-core
       description: Motherboard
       product: EA40_HB
       vendor: Acer
       physical id: 0
       version: Type2 - A01 Board Version
       serial: NBV9V110034261F4217600
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V1.01
          date: 04/14/2014
          size: 128KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 779MHz
          capacity: 779MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: ACR16D3LFS1KBG/2G
             vendor: Kingston
             physical id: 0
             serial: 552BDC79
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6AFR8A-PB
             vendor: Hynix
             physical id: 1
             serial: 1A2B7B87
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0b
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:65 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:4000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:67 memory:b0710000-b0713fff
        *-usb:0
             description: USB controller
             product: Lynx Point-LP USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:61 memory:b0700000-b070ffff
        *-communication
             description: Communication controller
             product: Lynx Point-LP HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:64 memory:b0718000-b071801f
        *-multimedia:1
             description: Audio device
             product: Lynx Point-LP HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:66 memory:b0714000-b0717fff
        *-pci:0
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:58 ioport:2000(size=4096) memory:9fb00000-9fcfffff ioport:9fd00000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:59 ioport:3000(size=4096) memory:b0600000-b06fffff ioport:b0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 0c
                serial: c4:54:44:95:f0:a1
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:63 ioport:3000(size=256) memory:b0600000-b0600fff memory:b0400000-b0403fff
        *-pci:2
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:60 memory:b0500000-b05fffff ioport:9ff00000(size=1048576)
           *-network
                description: Wireless interface
                product: AR9462 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: b0:10:41:04:6f:d7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-34-generic firmware=N/A ip=192.168.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:19 memory:b0500000-b057ffff memory:9ff00000-9ff0ffff
        *-usb:1
             description: USB controller
             product: Lynx Point-LP USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b071c000-b071c3ff
        *-isa
             description: ISA bridge
             product: Lynx Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Lynx Point-LP SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:62 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:b071b000-b071b7ff
        *-serial UNCLAIMED
             description: SMBus
             product: Lynx Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b0719000-b07190ff ioport:4040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10JPVX-22J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WX61E1461559
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=20095323-d2d6-42ec-8220-77c572098010 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: a73f-39bc
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: b4e99e1e-8c8e-409e-ba15-8bf882ded919
                size: 925GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-08-08 15:52:20 filesystem=ext4 lastmountpoint=/ modified=2014-09-01 19:55:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-09-01 19:55:34 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: d4b10993-a6a1-4f87-a6e8-d7ce0facf144
                size: 6065MiB
                capacity: 6066MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
```

---

