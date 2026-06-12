---
title: "Ubuntu Server new installation - screen pulses"
date: 2016-11-12
forum: Hardware
---

### Post by silverhawk184 on 2016-11-12
Hello, I am trying to give new live to an old laptop. 

I initially was wanting to install Chromium OS (Cloud Ready) on it but the screen was pulsing/flickering and made it unusable. It is hard to explain it is not the backlight, but the screen fades white. See the video below:
[https://goo.gl/photos/j8gLMAFgra7kJWWF7](https://goo.gl/photos/j8gLMAFgra7kJWWF7)

Thinking it was a driver issue and knowing that drivers are hard to come by with Chrome OS, I procceded to install my trusty backup, Ubuntu. The installation wizard displayed correctly but on the first boot into the new system, the screen started pulsing again. 
[https://goo.gl/photos/M1U3MgkfUAU6oGe99](https://goo.gl/photos/M1U3MgkfUAU6oGe99)


But windows 7 works perfectly on it.

Is there a way to fix this? I do not believe that the drivers are loaded or configurable at this point? Are they?

Thank you,
Nick


Ubuntu Server 16.10 on an older Dell 1647 with an ATI HD 3670.

Proof this laptop has been compatible with Ubuntu in the past.
[http://www.linlap.com/dell_studio_xps_16](http://www.linlap.com/dell_studio_xps_16)
[https://webcache.googleusercontent.com/search?q=cache:SVSYtnPHvPAJ:https://thegridgoodwill.com/product/ubuntu-dell-pp35l-2-66-ghz-320-gb-hd-4gb-ram/+&cd=2&hl=en&ct=clnk&gl=us](https://webcache.googleusercontent.com/search?q=cache:SVSYtnPHvPAJ:https://thegridgoodwill.com/product/ubuntu-dell-pp35l-2-66-ghz-320-gb-hd-4gb-ram/+&cd=2&hl=en&ct=clnk&gl=us)
[http://www.tomsguide.com/forum/53717-35-dell-1640-heat-problems](http://www.tomsguide.com/forum/53717-35-dell-1640-heat-problems)


UPDATE:
I ran a live cd and connected the laptop to a TV over HDMI and the TV displayed perfectly and fluid. Meanwhile the laptop screen would continue to freeze, flash and fade. My guess is there is a setting for the display in the Kernel and the refresh rate is too low. Is there an easy way to update the kernel's display settings?

---

### Post by silverhawk184 on 2016-11-17
*bump* Page 3 is too far back. Have not had any new views in a few days.

---

### Post by mörgæs on 2016-11-19
Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by silverhawk184 on 2016-12-06
Here is my lshw.txt

```

computer
    description: Portable Computer
    product: Studio XPS 1640
    vendor: Dell Inc.
    version: A153
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=portable frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0Y536R
       vendor: Dell Inc.
       physical id: 0
       version: A15
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A15
          date: 04/09/2011
          size: 113KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: CPU Version
          slot: U2E1
          size: 2667MHz
          capacity: 2667MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf eagerfpu pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority dtherm ida cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: burst internal write-back instruction
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1066 MHz (0.9 ns)
             product: EBJ21UE8BBS0-AE-F
             vendor: AMI
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1066 MHz (0.9 ns)
             product: EBJ21UE8BBS0-AE-F
             vendor: AMI
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:cfe00000-cfefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV730/M96-XT [Mobility Radeon HD 4670]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:30 memory:d0000000-dfffffff ioport:2000(size=256) memory:cfef0000-cfefffff memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: RV710/730 HDMI Audio [Radeon HD 4000 series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:33 memory:cfeec000-cfeeffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1820(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:fc404800-fc404bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Patriot Memory
                   physical id: 3
                   bus info: usb@1:3
                   logical name: scsi6
                   version: 1.10
                   serial: [REMOVED]
                   capabilities: usb-2.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=498mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Patriot Memory
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdb
                      logical name: /cdrom
                      version: PMAP
                      serial: [REMOVED]
                      size: 29GiB (31GB)
                      capabilities: removable
                      configuration: ansiversion=4 logicalsectorsize=512 mount.fstype=iso9660 mount.options=ro,noatime sectorsize=512 state=mounted
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                         logical name: /cdrom
                         size: 29GiB (31GB)
                         capabilities: partitioned partitioned:dos
                         configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=05e037df state=mounted
                       *-volume
                            description: Windows FAT volume
                            vendor: mkfs.fat
                            physical id: 2
                            logical name: /dev/sdb2
                            version: FAT12
                            serial: [REMOVED]
                            size: 15EiB
                            capabilities: primary boot fat initialized
                            configuration: FATs=2 filesystem=fat
              *-usb:1
                   description: Video
                   product: Laptop_Integrated_Webcam_2M
                   vendor: CN0TX6137248795FC64D
                   physical id: 6
                   bus info: usb@1:6
                   version: 89.08
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=168mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:fc400000-fc403fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f6000000-f7ffffff ioport:f0000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:f8000000-f9ffffff ioport:f2000000(size=33554432)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-22-generic firmware=8.83.5.1 build 33692 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:31 memory:f8000000-f8001fff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:5000(size=4096) memory:fa000000-fbffffff ioport:f4000000(size=33554432)
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:6000(size=4096) memory:fc000000-fc0fffff ioport:c0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetLink BCM5784M Gigabit Ethernet PCIe
                vendor: Broadcom Limited
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: enp8s0
                version: 10
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:34 memory:fc000000-fc00ffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fc404c00-fc404fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fc100000-fc1fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:09:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:fc100000-fc1007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:09:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:fc100800-fc1008ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:09:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:18 memory:fc101000-fc1010ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:09:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:18 memory:fc101400-fc1014ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:18f0(size=8) ioport:18e4(size=4) ioport:18e8(size=8) ioport:18e0(size=4) ioport:18c0(size=32) memory:fc404000-fc4047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0200000-c02000ff ioport:1c00(size=32)
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG SSD 830
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3B1Q
             serial: [REMOVED]
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=9c811612
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-09-27 03:09:19 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 119GiB
                capacity: 119GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-09-27 03:09:20 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW AD-7640S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: HD18
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
  *-battery
       product: SDI
       vendor: SDI
       physical id: 1
       slot: System Battery Bay
       capacity: 44000mWh
       configuration: voltage=11.1V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: outbound
  *-power UNCLAIMED
       description: To Be Defined By O.E.M
       product: To Be Defined By O.E.M
       vendor: To Be Defined By O.E.M
       physical id: 3
       version: 2.50
       serial: [REMOVED]
       capacity: 32768mWh


```

---

### Post by mörgæs on 2016-12-07
Since the hard disk is NTFS-formatted I guess this is a Windows single boot and that the lshw command is run from a live boot. This is fine.

The BIOS is also new. Check. 

The Radeon HD 4xxx series graphics cards normally works right away and I don't know of any tweaks necessary. Does it behave the same way in a live boot of Lubuntu?

---

### Post by silverhawk184 on 2016-12-07
It does it with Ubuntu Server ( see first post, 2nd link I believe) so I think running LXDE will have the same effect. I will try and update you in a few.

---

