---
title: "Possible power issues with 11.04"
date: 2011-07-17
forum: Hardware
---

### Post by M.pike on 2011-07-17
Hi all,

I am not exactly new to linux but i am anything but an expert so bear with me please.  Until recently I have been running Ubuntu 9 (not sure what 9.xx) as it was the only linux I could get working with my wireless (RT2870).  Finally got round to upgrading and I am now on 11.04 which works fine with my wireless but I now have another issue.

Every few minutes (the time interval changes betwen 1 min and 10 mins) it decides to turn off.  Its not like a shut down more like a suspend/hibernate except that it does it while i am in the middle of typing or using th mouse.  I have tried changing the power settings under "Power Management" to never sleep but it still does it.  It is really annoying cos I then need to press power to get it back on, re login and turn my wireless card back on, makes downloading anything of a moderate size all but impossible.

Not sure what information is required so I have stuck the output of lshw in, anything else can be supplied if required.  The laptop is not a very well know one, its a Zoostorm Freedom that was modified before I bought it to give it a full size Hard Drive and stuff.
```
martin                    
    description: Computer
    version: D0.05T45.17.20
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal family=Intel_Mobile sku=BasicNB_QS uuid=78563412-3412-3412-1122-334455667788
  *-core
       description: Motherboard
       product: 3310-9310
       vendor: Zoostorm
       physical id: 0
       version: D0.05T45.17.20
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: D0.05T45.17
          date: 04/18/2008
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: GMT10064SOX825-667
             vendor: 0x7F7F7F7F7F620000
             physical id: 0
             serial: 0x00000000
             slot: J2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1a
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm nx cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1b
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1c
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:54180000-541fffff ioport:40c0(size=8) memory:40000000-4fffffff memory:54200000-5423ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:54100000-5417ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:54240000-54243fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=8192) memory:53100000-540fffff ioport:50000000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:1a:13:b8:63:03
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:2000(size=256) memory:50010000-50010fff memory:50000000-5000ffff memory:50020000-5003ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:52100000-530fffff ioport:51100000(size=16777216)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:4060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:54244400-542447ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:40a0(size=16)
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2160B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K62KT972DD5M
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a0118112
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 264c6b69-749f-4b5c-951f-1eef61e92e76
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-04-19 21:15:45 filesystem=ext3 modified=2011-07-10 21:13:10 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2011-07-17 16:02:07 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2902MiB
                   capacity: 2902MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2902MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:4000(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1a:13:b3:5c:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-10-generic firmware=0.12 ip=192.168.1.3 link=yes multicast=yes wireless=IEEE 802.11bgn
```

Hope someone can help me with this, I kinda need the laptop as I have no desktop and I work in IT.  Thanks in advance.

Martin

---

### Post by M.pike on 2011-07-17
UPDATE:  occasionally when the issue strikes pressing the power does not start it back up again, I sometimes have to totally cut power (remove battery and mains) then restart it again, usually when this happens the issue strikes again around login time.

---

