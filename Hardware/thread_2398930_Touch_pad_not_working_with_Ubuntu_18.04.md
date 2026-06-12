---
title: "Touch pad not working with Ubuntu 18.04"
date: 2018-08-19
forum: Hardware
---

### Post by apverma13 on 2018-08-19
I've upgraded from Ubuntu 16.04 to 18.04 and since then I'm facing following 2 issues,

1. Touch pad is not working (however sometime while typing when my wrist goes over touch pad the cursor moves but it is random)
2. The in built speakers sound garbled but with Headphones plugged in sound is clear.

 While I was using stock Windows 8.1 last year there was this Dolby Home  Theater v.4 driver with which in built speakers were awesome. Is there  any alternate to it in Ubuntu 18.04?

When I run
```
sudo lshw -sanitize > lshw.txt
```

Output is,

```
computer
    description: Notebook
    product: IdeaPad Z585 (System SKU Number Unknown)
    vendor: LENOVO
    version: IdeaPad Z585
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=IdeaPad Z585 sku=System SKU Number Unknown uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Lenovo
       vendor: LENOVO
       physical id: 0
       version: 31900004WIN8 STD SGL
       serial: [REMOVED]
       slot: Chassis Location Unknown
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 60CN95WW
          date: 01/03/2013
          size: 128KiB
          capacity: 8128KiB
           capabilities: pci upgrade shadowing cdboot bootselect edd  int5printscreen int9keyboard int14serial int17printer int10video pc98  acpi usb biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: SHARETRONIC
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 [empty]
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 0
             width: 255 bits
     *-cpu
          description: CPU
          product: AMD A8-4500M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: f
          bus info: cpu@0
          version: AMD A8-4500M APU with Radeon(tm) HD Graphics
          slot: Socket FS1r2
          size: 1358MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 100MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht  syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl  nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma  cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm  extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop  skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb  cpb hw_pstate ssbd vmmcall bmi1 arat npt lbrv svm_lock nrip_save  tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold  cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 10
             slot: L1 Cache
             size: 192KiB
             capacity: 192KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 11
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-display
             description: VGA compatible controller
             product: Trinity [Radeon HD 7640G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:32 memory:d0000000-dfffffff ioport:3000(size=256) memory:f0300000-f033ffff memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Trinity HDMI Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f0344000-f0347fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f0200000-f02fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Thames [Radeon HD 7500M/7600M Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                 resources: irq:33 memory:e0000000-efffffff memory:f0200000-f021ffff  ioport:2000(size=256) memory:f0220000-f023ffff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:1000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 05
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw  ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:18 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-pci:2
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f0100000-f01fffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                 configuration: broadcast=yes driver=ath9k  driverversion=4.18.0-041800rc5-lowlatency firmware=N/A ip=[REMOVED]  latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:19 memory:f0100000-f017ffff memory:f0180000-f018ffff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0348000-f0349fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.18.0-041800rc5-lowlatency xhci-hcd
                physical id: 0
                bus info: usb@5
                logical name: usb5
                version: 4.18
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.18.0-041800rc5-lowlatency xhci-hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.18
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
              resources: irq:31 ioport:3118(size=8) ioport:3124(size=4)  ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16)  memory:f034c000-f034c7ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f034b000-f034bfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.18.0-041800rc5-lowlatency ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.18
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f034ca00-f034caff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.18.0-041800rc5-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.18
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   description: Video
                   product: Lenovo EasyCamera
                   vendor: LOEAAI011P2S01131X10546
                   physical id: 3
                   bus info: usb@1:3
                   version: 7.19
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f034a000-f034afff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.18.0-041800rc5-lowlatency ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.18
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: PixArt
                   physical id: 5
                   bus info: usb@4:5
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f034c900-f034c9ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.18.0-041800rc5-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.18
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   description: Generic USB device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 3
                   bus info: usb@2:3
                   version: 39.60
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f0340000-f0343fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-generic
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=sdhci-pci latency=71
             resources: irq:16 memory:f034c800-f034c8ff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0001
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=5069a304-3b73-40e1-a759-9202a2d05c57 logicalsectorsize=512 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 231GiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                 configuration: created=2018-06-23 09:24:57 filesystem=ext4  lastmountpoint=/ modified=2018-08-19 18:14:17 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro mounted=2018-08-19 18:14:23  state=mounted
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 499GiB
                capacity: 499GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-06-24 17:41:05 filesystem=ntfs name=Softwares state=clean
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: [REMOVED]
                size: 199GiB
                capacity: 199GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-06-24 17:48:03 filesystem=ntfs label=Movies & Music state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8D1
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 8.10
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

Please help me out getting Touch pad & Speakers functional again.
Thanks

---

### Post by uncielser456 on 2018-08-21
[COLOR=#242729][FONT=Arial]Maybe you should upgrade your kernel. Sometimes those lower kernels don't find the speakers and touchpad by default.[/FONT][/COLOR]

---

### Post by apverma13 on 2018-09-08
I checked the kernel version it was updated already. 

However some updates on 8 September from Ubuntu auto-updater did the trick and now touch pad is now "working."

Now may be someone can help with inbuilt speaker audio quality and 18.04 would be awesome again.

Thanks.

---

