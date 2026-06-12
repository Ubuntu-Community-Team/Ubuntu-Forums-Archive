---
title: "Aspire 5820TG Graphics problem"
date: 2010-10-17
forum: Hardware
---

### Post by hesselbom on 2010-10-17
Hello,

I don't know that much about this stuff so please bear with me.

I recently installed Ubuntu 10.10 on my Acer Aspire 5820TG laptop. After updating everything needed to I go to *System>Administration>Additional Driver*s and find *"ATI/AMD proprietary FGLRX graphics driver"*. I "activate" it but then when I restart my laptop I only get the console view, no screen at all. At this point I didn't know what to do so I reinstalled Ubuntu and haven't activated the driver after that.

Now, this isn't a big problem until I try to play some games. They all have incredible lag and I'm guessing it's due to not having a graphics driver installed.

I've searched through Google a bit, and wound up on several threads on this site, but couldn't find a solution and all I can think of is that either Ubuntu is showing me the wrong driver or that I have 2 graphics cards and the wrong one is used.

If anyone can help I'd be eternally grateful because it would mean I won't have to go back to Windows. :)

---

### Post by hesselbom on 2010-10-18
Also, this is my output from running "lshw":
```
hesselbom-paradise
    description: Computer
    product: Aspire 5820TG
    vendor: Acer
    version: V1.06
    serial: LXPTN021760170A8432500
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal uuid=6BAF1F97-19A7-4003-BE22-C80AA974822F
  *-core
       description: Motherboard
       product: ZR7B
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: 016QZOMBQTF00182
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: V1.06 (04/07/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: M471B5673EH1-CF8
             physical id: 0
             serial: 95BFEFE1
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 1
             serial: 00000000
             slot: DIMM1
             width: 8 bits
             clock: 1067MHz (0.9ns)
        *-bank:2
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: M471B5673EH1-CF8
             physical id: 2
             serial: 95BFEFF6
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: DIMM Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 3
             serial: 00000000
             slot: DIMM3
             width: 8 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 2a
          bus info: cpu@0
          version: 6.5.2
          serial: 0002-0652-0000-0000-0000-0000
          slot: CPU
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=1
        *-cache:0
             description: L3 cache
             physical id: 2b
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 2d
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 2e
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
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
     *-cache
          description: L1 cache
          physical id: 2c
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:dc400000-dc4fffff ioport:d0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: Redwood [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:d0000000-d7ffffff memory:dc400000-dc41ffff ioport:3000(size=256) memory:dc440000-dc45ffff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:48 memory:dc420000-dc423fff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 12
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4050(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:dc506100-dc50610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:dc505c00-dc505fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:dc500000-dc503fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:db400000-dc3fffff ioport:d8400000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: c8:0a:a9:74:82:2f
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:47 memory:db400000-db43ffff ioport:2000(size=128)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:da400000-db3fffff ioport:d9400000(size=16777216)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 78:e4:00:5c:1b:c0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:da400000-da40ffff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:dc505800-dc505bff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:4048(size=8) ioport:405c(size=4) ioport:4040(size=8) ioport:4058(size=4) ioport:4020(size=32) memory:dc505000-dc5057ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX81A10T9697
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a9c09bb8
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c4e6-541d
                   size: 12GiB
                   capacity: 13GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-05-05 15:07:20 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: bee7-b709
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-05-05 15:07:24 filesystem=ntfs label=SYSTEM RESERVED state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 182d0af3-43ca-7c46-8763-14506e7cd46e
                   size: 352GiB
                   capacity: 352GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-08-24 03:05:37 filesystem=ntfs label=Acer modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 99GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 476MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-U633F
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AC00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dc506000-dc5060ff ioport:4000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:21 memory:dc504000-dc504fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:7f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:7f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:7f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:7f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:7f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:7f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake
```

---

### Post by FelixII on 2011-01-23
I've got a similar problem with the same laptop model. This model has an onboard Intel HD graphics adapter and a dedicated Radeon 5650HD graphics adapter. Acer provides a Windows application to switch between both without reboot.

Ubuntu is working fine until I install the [I]proprietary ATI driver. After restart the console shows up and when I type "startx" I get error messages like "no devices detected" and "no screens found". I can bypass the error by going into BIOS and disabling the Intel HD chip (you can't disable the Radeon). But since this action decreases the battery life (under Windows 7) from 6-7 hours to 2-3 hours I would like to have the same switch option under Ubuntu.

Any ideas?
[/I]

---

### Post by adduds on 2011-03-02
After you install fglrx you have to go into bios and graphics --> discrete (normally set to switchable) 

it's annoying because everytime i switch over to win7 i have to switch it back to switchable in bios :@

then back to discrete for ubuntu grrrr

---

