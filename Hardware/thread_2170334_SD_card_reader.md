---
title: "SD card reader"
date: 2013-08-25
forum: Hardware
---

### Post by JorisSchellekens on 2013-08-25
I've never needed my SD card reader up until now.
And I've been forced to conclude it simply doesn't work.
Sadly enough, the driver (available for download at RealTek) does not compile due to errors.

Kind regards,
Joris

ps: I've included the output of sudo lshw, to give a fair indication of the exact hardware.

```

joris-hp-pavilion-g7-notebook-pc
    description: Notebook
    product: HP Pavilion g7 Notebook PC (D8Q20EA#UUG)
    vendor: Hewlett-Packard
    version: 088A120000305910000620100
    serial: 5CD3101SY1
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV sku=D8Q20EA#UUG uuid=35434433-3130-3153-5931-7446A07C0953
  *-core
       description: Motherboard
       product: 184C
       vendor: Hewlett-Packard
       physical id: 0
       version: 57.35
       serial: PCTXB028J4FAEB
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.27
          date: 04/12/2013
          size: 1MiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1U16BC4P2-B19H
             vendor: A-DATA Technology
             physical id: 0
             serial: 000058AD
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1U16BC4P2-B19H
             vendor: A-DATA Technology
             physical id: 1
             serial: 0000587A
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: AMD A6-4400M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 27
          bus info: cpu@0
          version: AMD A6-4400M APU with Radeon(tm) HD Graphics
          serial: NotSupport
          slot: Socket FT1
          size: 1400MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 28
             slot: L1 Cache
             size: 96KiB
             capacity: 96KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 29
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: Trinity [Radeon HD 7520G]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:51 memory:d0000000-dfffffff ioport:4000(size=256) memory:f0400000-f043ffff
        *-multimedia:0
             description: Audio device
             product: Trinity HDMI Audio Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:f0444000-f0447fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:f0300000-f03fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Thames XT [Radeon HD 7670M]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:52 memory:e0000000-efffffff memory:f0300000-f031ffff ioport:3000(size=256) memory:f0320000-f033ffff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: RT3290 Wireless 802.11n 1T/1R PCIe
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: b8:76:3f:29:36:45
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-29-generic firmware=0.37 ip=192.168.0.135 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:f0210000-f021ffff
           *-generic UNCLAIMED
                description: Bluetooth
                product: RT3290 Bluetooth
                vendor: Ralink corp.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f0200000-f020ffff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0448000-f0449fff
        *-usb:1
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:f044a000-f044bfff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:48 ioport:4118(size=8) ioport:4124(size=4) ioport:4110(size=8) ioport:4120(size=4) ioport:4100(size=16) memory:f0450000-f04507ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f044f000-f044ffff
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f044e000-f044e0ff
        *-usb:4
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f044d000-f044dfff
        *-usb:5
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f044c000-f044c0ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f0440000-f0443fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-pci:3
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0100000-f01fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:49 memory:f0100000-f0100fff
        *-pci:4
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f0000000-f00fffff
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 05
                serial: 74:46:a0:7c:09:53
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:47 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
          vendor: Advanced Micro Devices [AMD]
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
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Advanced Micro Devices [AMD]
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
             version: 2AR1
             serial: S2SWJ9KCC01810
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=1a12cec4-0606-4f49-a1d4-69629f24b606 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: d8d5-2393
                size: 93MiB
                capacity: 93MiB
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
                serial: d71afcdb-fb6a-479d-a872-e00ae632b818
                size: 923GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-19 23:46:21 filesystem=ext4 lastmountpoint=/ modified=2013-08-24 18:44:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-08-24 18:44:14 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: a88c812c-f3b9-4d7e-8fc4-d91daafac3f5
                size: 7648MiB
                capacity: 7649MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT80N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: R102
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: 13-12
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V

```

---

### Post by Dennis N on 2013-08-25
Mine (the built-in one) won't work either on one computer we have. Solution: bought a USB Targus SD (and related formats) card reader for about $5. It has never failed to work. Plug in and use. Wal*Mart (in U.S.A.) and other shops.

Probably not the solution you are looking for, however.

---

### Post by JorisSchellekens on 2013-08-25
That's the one thing I generally dislike about these fora, peoply trying to modify your original question :-p
It is indeed, not quite the solution I'm after.

Thank you for putting in the time and effort to reply though.

---

### Post by coldraven on 2013-08-26
What is the output from ```
lsusb
```

---

### Post by JorisSchellekens on 2013-08-27
output of sudo lsusb, as requested:

```

Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

This command was executed without any medium inserted in the card reader.

Kind regards,
Joris

---

