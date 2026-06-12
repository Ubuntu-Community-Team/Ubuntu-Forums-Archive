---
title: "Touchpad not detected on HP 255 G2."
date: 2017-06-04
forum: Hardware
---

### Post by m1ksu on 2017-06-04
Title pretty much explains it all. The touchpad is not being detected, thus, it doesn't work. But, some times, it does work. Or it did. I don't know what caused it to function in the past, but it dies after a restart. If I get any help on this, thank you.

---

### Post by mörgæs on 2017-06-05
Hi, welcome to the fora.
Let's see more about the hardware. Please copy the command ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, execute it and post the results in CODE tags.

---

### Post by m1ksu on 2017-06-05
```

computer
    description: Notebook
    product: HP 255 G2 Notebook PC (F0Z61EA#UUW)
    vendor: Hewlett-Packard
    version: 0974100000405F10000620181
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N L=SMB B=HP S=255 sku=F0Z61EA#UUW uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 2192
       vendor: Hewlett-Packard
       physical id: 0
       version: 41.18
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.07
          date: 11/13/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb uefi
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: [REMOVED]
             slot: Bottom-Slot 1(top)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1334 MHz (0,7 ns)
             product: HP16D3LS1KFG/4G
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 1334MHz (0.7ns)
     *-cpu
          description: CPU
          product: AMD E1-2100 APU with Radeon(TM) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 28
          bus info: cpu@0
          version: AMD E1-2100 APU with Radeon(TM) HD Graphics
          serial: [REMOVED]
          slot: Socket FT1
          size: 900MHz
          capacity: 1GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_l2 hw_pstate proc_feedback vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 29
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 2a
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
     *-pci:0
          description: Host bridge
          product: Family 16h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Kabini [Radeon HD 8210]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:36 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0c00000-f0c3ffff memory:f0c60000-f0c7ffff
        *-multimedia:0
             description: Audio device
             product: Kabini HDMI/DP Audio
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:37 memory:f0c40000-f0c43fff
        *-pci:0
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:f0b00000-f0bfffff ioport:f0d00000(size=2097152)
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:31 memory:f0b00000-f0b00fff
        *-pci:1
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f0a00000-f0afffff ioport:f0800000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eno1
                version: 07
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:33 ioport:2000(size=256) memory:f0a00000-f0a00fff memory:f0800000-f0803fff
        *-pci:2
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:f0900000-f09fffff ioport:f0f00000(size=2097152)
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlo1
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.4.0-62-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:38 memory:f0900000-f097ffff memory:f0980000-f098ffff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0c48000-f0c49fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-62-generic xhci-hcd
                physical id: 0
                bus info: usb@6
                logical name: usb6
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-62-generic xhci-hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:34 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:f0c4e000-f0c4e3ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0c4d000-f0c4dfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-62-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   vendor: Primax
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Atheros Communications, Inc.
                   physical id: 2
                   bus info: usb@3:2
                   version: 0.02
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0c4c000-f0c4c0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-62-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Video
                   product: HP Truevision HD
                   vendor: Chicony Electronics Co., Ltd.
                   physical id: 3
                   bus info: usb@1:3
                   version: 69.21
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0c4b000-f0c4bfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-62-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0c4a000-f0c4a0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-62-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f0c44000-f0c47fff
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
     *-pci:1
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 16h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 16h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 16h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 16h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 16h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
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
             product: ST500LT012-1DG14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: YAM1
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=45850f4a-29c0-4b22-a579-34cc451d349d logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 461GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-02-18 13:44:18 filesystem=ext4 lastmountpoint=/ modified=2017-06-04 19:00:03 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-06-04 19:00:16 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 3545MiB
                capacity: 3545MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GU90N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: U900
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: OA04041
       vendor: 13-42
       physical id: 1
       version: NULL
       serial: [REMOVED]
       slot: Primary
       capacity: 41440mWh
       configuration: voltage=14,8V

```

---

### Post by m1ksu on 2017-06-05
```
 lshal -u "$(hal-find-by-capability --capability input.touchpad)" 
``` also returns nothing.

---

### Post by mörgæs on 2017-06-06
It would be interesting to see if a newer kernel works better. You could try a live boot of 17.04 for comparison.

---

### Post by gsahli on 2017-06-06
I wonder if making an entry in /etc/X11/xorg.conf (or, a file in /etc/X11/xorg.conf.d) will get it recognized?
examples:
[https://wiki.debian.org/SynapticsTouchpad](https://wiki.debian.org/SynapticsTouchpad)
or
[https://wiki.gentoo.org/wiki/Synaptics](https://wiki.gentoo.org/wiki/Synaptics)

---

### Post by m1ksu on 2017-06-08
Xubuntu 17 didn't help. The problem stays.

---

