---
title: "ubuntu 17.10 dual monitor problem"
date: 2017-11-06
forum: Hardware
---

### Post by kev97 on 2017-11-06
hi i have upgraded to ubuntu 17.10 
iv used ubuntu for a while and can normaly sort out any probs but im stuck
with this. when i plug a hdmi cable into my intell laptop to use the dual monitor display
to watch videos on my hd tv i get a blinking on both screens then it eventualy looses signal 
i have dual boot with earlier 16.04 and it works perfect 
as soon as i boot to 17.10 the blinking,flickering starts making laptop unuseable untill i unplug cable
i have had similar problems in past but have always been able to fix by ajusting resolution or drivers
but im stuck as everything iv tried wont work 
any help please..thanks

---

### Post by sebakerckhof on 2017-11-08
Got the same problem. Also worked fine under 16.04. Although the blinking does stop after a while. It seems to need like 4 or 5 iterations where the screens go black and back on.

---

### Post by coffeecat on 2017-11-08
*Thread moved to **Hardware**.*

---

### Post by mörgæs on 2017-11-09
Please both: Copy and paste the command ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags.

---

### Post by hydrarulz2 on 2017-11-12
```

computer                    
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Maximus IV GENE-Z
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3603
          date: 11/09/2012
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          serial: [REMOVED]
          slot: LGA1155
          size: 1659MHz
          capacity: 5900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
             configuration: level=2
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 54
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ16GX3M4A1600C9
             vendor: AMI
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ16GX3M4A1600C9
             vendor: AMI
             physical id: 1
             serial: [REMOVED]
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ16GX3M4A1600C9
             vendor: AMI
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: CMZ16GX3M4A1600C9
             vendor: AMI
             physical id: 3
             serial: [REMOVED]
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=snb_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GM204 [GeForce GTX 970]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GM204 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-display UNCLAIMED
             description: Display controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:42 memory:f7b2c000-f7b2c00f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eno1
             version: 05
             serial: [REMOVED]
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:41 memory:f7b00000-f7b1ffff memory:f7b29000-f7b29fff ioport:f080(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7b28000-f7b283ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-16-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0
                      description: Mouse
                      product: Gaming Mouse G502
                      vendor: Logitech
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 3.02
                      serial: [REMOVED]
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=300mA speed=12Mbit/s
                 *-usb:1
                      description: USB hub
                      product: USB2.0 Hub
                      vendor: Genesys Logic, Inc.
                      physical id: 5
                      bus info: usb@1:1.5
                      version: 8.01
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                    *-usb:0
                         description: Keyboard
                         product: G19 Gaming Keyboard
                         vendor: Logitech, Inc.
                         physical id: 1
                         bus info: usb@1:1.5.1
                         version: 1.10
                         capabilities: usb-2.00
                         configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
                    *-usb:1
                         description: Human interface device
                         product: G19 Gaming Keyboard
                         vendor: Logitech
                         physical id: 2
                         bus info: usb@1:1.5.2
                         version: 0.23
                         capabilities: usb-2.00
                         configuration: driver=usbhid speed=480Mbit/s
                 *-usb:2
                      description: Video
                      product: Microsoft
                      vendor: Microsoft
                      physical id: 6
                      bus info: usb@1:1.6
                      version: 1.06
                      capabilities: usb-2.00
                      configuration: driver=snd-usb-audio maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f7b20000-f7b23fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:cfb00000-cfcfffff ioport:cfd00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f7a00000-f7afffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:f7a00000-f7a07fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.13.0-16-lowlatency xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.13
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.13.0-16-lowlatency xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.13
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7900000-f79fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:f7900000-f7907fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.13.0-16-lowlatency xhci-hcd
                   physical id: 0
                   bus info: usb@5
                   logical name: usb5
                   version: 4.13
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.13.0-16-lowlatency xhci-hcd
                   physical id: 1
                   bus info: usb@6
                   logical name: usb6
                   version: 4.13
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:d000(size=4096) memory:f7800000-f78fffff
           *-storage
                description: SATA controller
                product: JMB362 SATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:18 ioport:d040(size=8) ioport:d030(size=4) ioport:d020(size=8) ioport:d010(size=4) ioport:d000(size=16) memory:f7810000-f78101ff memory:f7800000-f780ffff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7b27000-f7b273ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-16-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb:0
                      description: Generic USB device
                      product: Xbox 360 Wireless Receiver for Windows
                      physical id: 3
                      bus info: usb@2:1.3
                      version: 1.00
                      serial: [REMOVED]
                      capabilities: usb-2.00
                      configuration: driver=xpad maxpower=260mA speed=12Mbit/s
                 *-usb:1
                      description: Modem
                      product: SAMSUNG_Android
                      vendor: SAMSUNG
                      physical id: 5
                      bus info: usb@2:1.5
                      version: 4.00
                      serial: [REMOVED]
                      capabilities: usb-2.00 atcommands
                      configuration: driver=cdc_acm maxpower=48mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Z68 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:f7b26000-f7b267ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7b25000-f7b250ff ioport:580(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1002FAEX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1D05
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=1f32abbe
           *-volume UNCLAIMED
                description: SFS partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                capacity: 931GiB
                capabilities: primary
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: KINGSTON SUV400S
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 96R9
             serial: [REMOVED]
             size: 223GiB (240GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=8f92d8e1
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                logical name: /var/lib/docker/plugins
                logical name: /var/lib/docker/aufs
                version: 1.0
                serial: [REMOVED]
                size: 207GiB
                capacity: 207GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-09-08 13:50:56 filesystem=ext4 lastmountpoint=/ modified=2017-11-12 23:04:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-11-12 23:02:21 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                size: 15GiB
                capacity: 15GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap volume
                   physical id: 5
                   logical name: /dev/sdb5
                   version: 1
                   serial: [REMOVED]
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: KINGSTON SV300S3
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: BBF0
             serial: [REMOVED]
             size: 223GiB (240GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=ab38a4dc
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                version: 3.1
                serial: [REMOVED]
                size: 223GiB
                capacity: 223GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2016-02-12 01:23:06 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdc2
                version: 3.1
                serial: [REMOVED]
                size: 445MiB
                capacity: 450MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2016-09-24 14:42:59 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:3
          physical id: 5
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABF0
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 3M
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=67e01a60
           *-volume
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                capacity: 465GiB
                capabilities: primary
     *-scsi:4
          physical id: 6
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1002FAEX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sde
             version: 1D05
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=d125d797
           *-volume UNCLAIMED
                description: SFS partition
                physical id: 1
                bus info: scsi@4:0.0.0,1
                capacity: 931GiB
                capabilities: primary
  *-power:0 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh
  *-power:1 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh
  *-network:0
       description: Ethernet interface
       physical id: 3
       logical name: docker0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=[REMOVED] link=no multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 4
       logical name: br-2de3da284d00
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=[REMOVED] link=no multicast=yes




```

---

### Post by mörgæs on 2017-11-13
A third poster, welcome. Fine if you all have more or less similar hardware but if the hardware is fundamentally different a moderator is going to split the posts.

You have dual graphics, Intel and Nvidia. I am not familiar with this but let's hope someone else has an idea.

---

