---
title: "Ubuntu 16.10 Live DVD : &quot;system running in low-graphics mode&quot;"
date: 2016-10-14
forum: Hardware
---

### Post by dlalonde2 on 2016-10-14
I wanted to install Ubuntu 16.10 but, after 10 tries now, I was never able to boot into Unity. I get the "system running in low-graphics mode" error and nothing happens no matter what I do.


Is there anything I can do or does this mean that starting with 16.10 I can't install Ubuntu anymore?


I tried running with nomodeset as described here: How do I solve "System is running in low graphics issue" in Ubuntu INSTALLER ?


But I ended up with a screen filled with a bunch of lines looking like this:


> [ 1575.552527] intel ips 0000:00:1f.6: failed to disable graphics turbo


Am I better to just give up and skip this version?


Thanks!

---

### Post by mörgæs on 2016-10-15
Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by dlalonde2 on 2016-10-15
OK strange thing, while I was doing what you asked, it worked but only ONCE and I was able to install it and boot. But since then, I've tried 3 times with the Live DVD and it still doesn't work. So here's the result you asked for (cause I could need to reinstall as I like to tinker with it): 

```
computer
    description: Notebook
    product: HP EliteBook 8440p (SJ047UP#ABA)
    vendor: Hewlett-Packard
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=SJ047UP#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 172A
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 30.34
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 9
          version: 68CCU Ver. D.23
          date: 06/14/2013
          size: 64KiB
          capacity: 3008KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
          slot: CPU 1
          size: 1333MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida arat cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 3
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5673FH0-CH9
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: Top-Slot 1(top)
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: ACR256X64D3S1333C9
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: Top-Slot 2(under)
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5058(size=8) memory:c0000-dffff
        *-communication:0
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:30 memory:d4724000-d472400f
        *-communication:1
             description: Serial controller
             product: 5 Series/3400 Series Chipset KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:5050(size=8) memory:d472b000-d472bfff
        *-network
             description: Ethernet interface
             product: 82577LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 05
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.12-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:28 memory:d4700000-d471ffff memory:d472a000-d472afff ioport:5020(size=32)
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d4729000-d47293ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb UNCLAIMED
                      description: Generic USB device
                      product: VFS451 Fingerprint Reader
                      vendor: Validity Sensors, Inc.
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 0.72
                      serial: [REMOVED]
                      capabilities: usb-1.10
                      configuration: maxpower=100mA speed=12Mbit/s
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:d4720000-d4723fff
        *-pci:0
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
             resources: irq:24 memory:d4600000-d46fffff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=8192) memory:d0600000-d45fffff ioport:d4900000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:d0500000-d05fffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6200
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:43:00.0
                logical name: wlo1
                version: 35
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-22-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:31 memory:d0500000-d0501fff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:d4728000-d47283ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 72.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
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
             resources: ioport:2000(size=4096) memory:d0400000-d04fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:44:06.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:d0401000-d04017ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:44:06.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d0403000-d04030ff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:44:06.2
                version: bb
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b04845440-b0484543f irq:22 memory:d0400000-d0400fff ioport:2000(size=256) ioport:2400(size=256) memory:d8000000-dbffffff memory:dc000000-dfffffff
        *-isa
             description: ISA bridge
             product: QM57 Chipset LPC Interface Controller
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
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:5048(size=8) ioport:5064(size=4) ioport:5040(size=8) ioport:5060(size=4) ioport:5000(size=32) memory:d4727000-d47277ff
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
             resources: irq:18 memory:d4726000-d4726fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST250LT007-9ZV14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: DEM1
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=e3789339
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 40GiB
                capacity: 40GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2016-10-15 12:27:43 filesystem=ext4 lastmountpoint=/ modified=2016-10-15 12:45:27 mounted=2016-10-15 12:45:32 state=clean
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 4211MiB
                capacity: 4211MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /media/fichiers
                version: 1.0
                serial: [REMOVED]
                size: 188GiB
                capacity: 188GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-10-15 02:01:36 filesystem=ext4 lastmountpoint=/home modified=2016-10-15 14:52:01 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2016-10-15 14:52:01 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7711H
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /cdrom
             version: 1.82
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=05e037df state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 2
                   version: FAT12
                   serial: [REMOVED]
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
  *-battery
       product: TD06055
       vendor: DP-SAN51
       physical id: 1
       slot: Primary
       capacity: 5100mWh
       configuration: voltage=10.8V
```

---

### Post by dlalonde2 on 2016-10-16
> **mörgæs said:**
> Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Do you have everything you need? :)

---

### Post by mörgæs on 2016-10-17
Yes and no. I have enough to see all about the hardware but I am not familiar with this type of graphical processor. 

Anyone else?

---

