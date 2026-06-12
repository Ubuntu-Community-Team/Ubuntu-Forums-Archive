---
title: "Kernel USB stack hangs, all USB ports stop operating"
date: 2020-11-23
forum: Hardware
---

### Post by jwbrase on 2020-11-23
I've recently been experiencing an issue with the kernel USB stack crashing. I had at first identified this as an Xorg crash that seemed to be an interaction between Xorg, the proprietary NVidia drivers, and Xscreensaver using graphics power management features, because it seemed to mostly happen when the machine had been idle and xscreensaver had put the monitor to sleep, and on previous Ubuntu versions, I actually had had X crashes related to driver issues on this hardware. The symptoms of the USB crash are similar, because there is a lack of response to input in both situations (and, when the monitor has been put to sleep, any non-input dependent moving output won't be displayed either).

I had a crash today while I was actually using the machine. The optical tracking LED for the mouse was not lit, and there was no response to keyboard input, including the Num/Scroll/Capslock not responding to the corresponding keys. While I was at another computer investigating the logs over ssh, I looked back over and noticed that xscreensaver had activated, which meant that the graphics stack was still running and not just displaying the last image from before the crash, allowing me to rule out an Xorg crash. Inspecting the kernel log turned up a whole bunch of stack traces with "usb" and "xhci" in the function names, and a message along the lines of "INFO: task kworker/3:3:1774607 blocked for more than 120 seconds." in most/all of them (about half had apcupsd instead of kworker, as I was using an APC UPS [see note at end of post]). There were messages about problems with /dev/sdc (a USB mounted backup drive).

Has anyone encountered a similar issue to this? I haven't been able to find search terms that turn up much on Google, and I'd like to see if the bug has been reported anywhere before filing my own bug report.

The machine is running Ubuntu 20.04, and I believe the issue had been occurring on 18.04 as well, but at the time I thought it was a graphics stack bug.

The machine was custom built about six years ago.

lshw output, with hostname, username, MAC, etc, redacted, as well as some tun/tap and bridge interfaces removed at the end of the output that don't correspond to physical hardware:

```
[hostname redacted]                     
    description: Desktop Computer
    product: MS-7850 (To be filled by O.E.M.)
    vendor: MSI
    version: 1.0
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To be filled by O.E.M. uuid=[redacted]
  *-core
       description: Motherboard
       product: Z87-G41 PC Mate(MS-7850)
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V1.4
          date: 09/18/2013
          size: 64KiB
          capacity: 8MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Xeon(R) CPU E3-1220 v3 @ 3.10GHz
          vendor: Intel Corp.
          physical id: 3d
          bus info: cpu@0
          version: Intel(R) Xeon(R) CPU E3-1220 v3 @ 3.10GHz
          slot: SOCKET 0
          size: 2705MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L2 cache
             physical id: 3e
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
             configuration: level=2
        *-cache:1
             description: L1 cache
             physical id: 3f
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back
             configuration: level=1
        *-cache:2
             description: L3 cache
             physical id: 40
             slot: CPU Internal L3
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 32GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C10D3/8GX
             vendor: Kingston
             physical id: 0
             serial: [redacted]
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C10D3/8GX
             vendor: Kingston
             physical id: 1
             serial: [redacted]
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C10D3/8GX
             vendor: Kingston
             physical id: 2
             serial: [redacted]
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C10D3/8GX
             vendor: Kingston
             physical id: 3
             serial: [redacted]
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v3 Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GM107 [GeForce GTX 750 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:35 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GM107 High Definition Audio Controller [GeForce 940MX]
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:30 memory:f7300000-f730ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-53-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=14 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: Dell USB Entry Keyboard
                   vendor: Dell
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.15
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Human interface device
                   product: CP1500AVRLCDa
                   vendor: CPS
                   physical id: 2
                   bus info: usb@3:2
                   version: 2.00
                   serial: CTHKU2000136
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=2mA speed=12Mbit/s
              *-usb:2
                   description: Mouse
                   product: Microsoft USB Optical Mouse
                   vendor: PixArt
                   physical id: 3
                   bus info: usb@3:3
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:3
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: VIA Labs, Inc.
                   physical id: a
                   bus info: usb@3:a
                   version: 90.90
                   capabilities: usb-2.10
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Human interface device
                      product: PC Game Controller
                      physical id: 1
                      bus info: usb@3:a.1
                      version: 1.09
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
                 *-usb:1 UNCLAIMED
                      description: Generic USB device
                      product: Microsoft
                      vendor: Microsoft
                      physical id: 2
                      bus info: usb@3:a.2
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: maxpower=260mA speed=12Mbit/s
                 *-usb:2
                      description: USB hub
                      product: USB2.0 Hub
                      vendor: VIA Labs, Inc.
                      physical id: 3
                      bus info: usb@3:a.3
                      version: 90.90
                      capabilities: usb-2.10
                      configuration: driver=hub slots=4 speed=480Mbit/s
                    *-usb:0
                         description: Generic USB device
                         product: F5U109/F5U409 PDA Adapter
                         vendor: Belkin USB PDA Adapter
                         physical id: 2
                         bus info: usb@3:a.3.2
                         version: 1.02
                         serial: 269671
                         capabilities: usb-1.10
                         configuration: driver=mct_u232 maxpower=100mA speed=12Mbit/s
                    *-usb:1
                         description: Human interface device
                         product: T.Flight Hotas X
                         vendor: Thrustmaster
                         physical id: 3
                         bus info: usb@3:a.3.3
                         version: 1.00
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=80mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-53-generic xhci-hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB3.0 Hub
                   vendor: VIA Labs, Inc.
                   physical id: 1
                   bus info: usb@4:1
                   version: 90.91
                   capabilities: usb-3.00
                   configuration: driver=hub slots=4 speed=5000Mbit/s
                 *-usb
                      description: USB hub
                      product: USB3.0 Hub
                      vendor: VIA Labs, Inc.
                      physical id: 3
                      bus info: usb@4:1.3
                      version: 90.91
                      capabilities: usb-3.00
                      configuration: driver=hub slots=4 speed=5000Mbit/s
              *-usb:1
                   description: Mass storage device
                   product: My Book 25EE
                   vendor: Western Digital
                   physical id: 2
                   bus info: usb@4:2
                   logical name: scsi6
                   version: 40.04
                   serial: [redacted]
                   capabilities: usb-3.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=8mA speed=5000Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: My Book 25EE
                      vendor: WD
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdc
                      version: 4004
                      serial: [redacted]
                      size: 3726GiB (4TB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: ansiversion=6 guid=[redacted] logicalsectorsize=512 sectorsize=4096
                    *-volume
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 1
                         bus info: scsi@6:0.0.0,1
                         logical name: /dev/sdc1
                         logical name: /media/[redacted]/Backup
                         version: 1.0
                         serial: [redacted]
                         size: 3726GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                         configuration: created=2016-12-07 21:38:08 filesystem=ext4 label=Backup lastmountpoint=/media/[redacted]/Backup modified=2020-11-23 06:43:21 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime mounted=2020-11-23 06:43:21 state=mounted
                 *-enclosure UNCLAIMED
                      description: SCSI Enclosure
                      product: SES Device
                      vendor: WD
                      physical id: 0.0.1
                      bus info: scsi@6:0.0.1
                      version: 4004
                      serial: [redacted]
                      configuration: ansiversion=6
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:33 memory:f731a000-f731a00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7318000-f73183ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-53-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.05
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f7310000-f7313fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:f2200000-f23fffff ioport:f2400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) memory:f7200000-f72fffff ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 0c
                serial: [redacted]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:17 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                resources: iomemory:202001f10-202001f0f
        *-pci:4
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 memory:f7100000-f71fffff
           *-network
                description: Wireless interface
                product: AR9287 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlp6s0
                version: 01
                serial: c0:4a:00:5e:32:ce
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=5.4.0-53-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:19 memory:f7100000-f710ffff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7317000-f73173ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-53-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.05
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Z87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-sata
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:31 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7316000-f73167ff
           *-disk:0
                description: ATA Disk
                product: TOSHIBA DT01ACA2
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ABB0
                serial: Y3NSWRPGS
                size: 1863GiB (2TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=[redacted] logicalsectorsize=512 sectorsize=4096
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /home
                   version: 1.0
                   serial: [redacted]
                   size: 1863GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-04-03 01:05:52 filesystem=ext4 label=Home lastmountpoint=/home modified=2020-11-23 06:37:01 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-11-23 06:37:01 state=mounted
           *-disk:1
                description: ATA Disk
                product: TOSHIBA DT01ACA2
                vendor: Toshiba
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: ABB0
                serial: Y3NSWTEGS
                size: 1863GiB (2TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=[redacted] logicalsectorsize=512 sectorsize=4096
              *-volume:0 UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   version: FAT32
                   serial: d96e-e98c
                   size: 188MiB
                   capacity: 189MiB
                   capabilities: boot fat initialized
                   configuration: FATs=2 filesystem=fat name=EFI System Partition
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   logical name: /
                   version: 1.0
                   serial: [redacted]
                   size: 266GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2020-10-04 05:35:44 filesystem=ext4 lastmountpoint=/ modified=2020-11-23 06:36:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2020-11-23 06:36:51 state=mounted
              *-volume:2
                   description: LVM Physical Volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   serial: [redacted]
                   size: 1330GiB
                   capacity: 1330GiB
                   capabilities: multi lvm2
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sdb4
                   logical name: /media/[redacted]/[redacted]
                   version: 1.0
                   serial: [redacted]
                   size: 266GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2017-02-08 10:42:31 filesystem=ext4 lastmountpoint=/media/[redacted]/[redacted] modified=2020-11-23 06:39:10 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime mounted=2020-11-23 06:39:10 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD Writer 1265v
                vendor: HP
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: CH21
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:18 memory:f7315000-f73150ff ioport:f000(size=32)
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0b00
          physical id: 3
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:03
          product: PnP device INT3f0d
          vendor: Interphase Corporation
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0501
          physical id: 6
          capabilities: pnp
          configuration: driver=serial
     *-pnp00:06
          product: PnP device PNP0400
          physical id: 7
          capabilities: pnp
          configuration: driver=parport_pc
     *-pnp00:07
          product: PnP device PNP0c02
          physical id: 8
          capabilities: pnp
          configuration: driver=system
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

```

[note] At the time this particular crash occured, the machine was connected to an APC UPS, and had apcupsd installed. I had already bought a UPS from a different manufacturer, and planned to switch to that UPS at next shutdown (the dataline protection on the old UPS only supported 10/100 ethernet, and we recently installed gigabit ethernet wiring in the house). The crash necessitated a shutdown, so I installed the new UPS and removed apcupsd when I rebooted. I'm inclined to think that apcupsd was a victim of the USB stack crashing, not the cause, but given that it features in about every other stack trace in kern.log, I have mentioned it for completeness. It, and the old UPS, will no longer be part of the machine configuration, however.

---

