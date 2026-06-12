---
title: "Wired ethernet is buggy on Ubuntu"
date: 2012-04-22
forum: Hardware
---

### Post by jesushero on 2012-04-22
I've got a toshiba satellite with ubuntu 10.04. I've had a LAN with no internet which works fine. I've also been able to connect to most wifi networks fine. But now I'm sharing internet with a friend, and although I can connect to the modem via wifi, the connection drops all the time and needs a hard-reset of the wifi card to connect again. 

So we thought we would try a wired connection to the modem, via ethernet. It just won't work. The green light on the ethernet port flashes on and off, and then the port seems to go to sleep until the next reboot. 

The daemon.log:

```
Apr 23 01:11:05 tosh NetworkManager: <info>  (wlan0): device state change: 3 -> 2 (reason 0)
Apr 23 01:11:05 tosh NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Apr 23 01:11:06 tosh NetworkManager: <info>  WiFi now enabled by radio killswitch
Apr 23 01:11:06 tosh NetworkManager: <info>  (wlan0): bringing up device.
Apr 23 01:11:06 tosh NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Apr 23 01:11:06 tosh NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Apr 23 01:11:07 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:11:07 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:11:07 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:12:00 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:12:00 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:12:01 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:12:01 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:12:01 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:12:03 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:12:03 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:12:04 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:12:04 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:12:04 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:12:05 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:12:05 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:12:06 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:12:06 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:12:06 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:12:07 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:12:07 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:12:09 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:12:09 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:12:09 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:12:10 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:12:10 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:12:11 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:12:11 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:12:11 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:12:12 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:12:12 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:12:13 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:12:13 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:12:13 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:13:15 tosh avahi-daemon[546]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.45.252.
Apr 23 01:13:15 tosh avahi-daemon[546]: New relevant interface eth0.IPv4 for mDNS.
Apr 23 01:13:15 tosh avahi-daemon[546]: Registering new address record for 169.254.45.252 on eth0.IPv4.
Apr 23 01:14:29 tosh NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 23 01:14:29 tosh NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 23 01:14:30 tosh NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Apr 23 01:14:30 tosh NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Apr 23 01:14:30 tosh NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 23 01:14:30 tosh avahi-daemon[546]: Withdrawing address record for 169.254.45.252 on eth0.
Apr 23 01:14:30 tosh avahi-daemon[546]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.45.252.
Apr 23 01:14:30 tosh avahi-daemon[546]: Interface eth0.IPv4 no longer relevant for mDNS.
```

It seems like the modem, a Thomson TG 585 v7, is not compatible with the networking on this laptop, or incompatible with ubuntu. All other modems work fine, both wired and wireless. 

What is more annoying, is that my friend showed up with a windows 7 laptop, and it connected straight away, both wired and wireless, with no set up and no problems. 

This is my millionth or so, big problem, with Ubuntu 10.04. It is actually so many problems piling up that I simply don't have the time to fix them. I've managed to live with most of them, but not having internet is out of the question of "living with".. 

If I can't fix that within the next day or two, then it's a permanent move away from Ubuntu for me and my 6 computers. I've tried 3 of the 6 computers so far with the ethernet cable, and they all do the same. So it seems like an Ubuntu problem, more than a hardware issue, since all computers are very different and two are desktops. They all work fine on a LAN together.

I'm considering switching to either another GNU/Linux distro, or FreeBSD, or just chucking the whole lot out and getting a mac to work on. I will not go back to Windows, no matter what, but I really can't afford to stay on Ubuntu. It is a huge money and time pit.

In the past couple of months, I've lost countless clients due to being unable to complete work because Ubuntu had some sort of bug with something, or broken packages, or crashed, or whatever..

Any help would be much appreciated.

lshw:

```
tosh                      
    description: Computer
    product: Satellite U300
    vendor: TOSHIBA
    version: PSU30E-03D01JGE
    serial: X7073755W
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=4030C1E7-A089-D811-BB6E-001B24BA5123
  *-core
       description: Motherboard
       product: Satellite U300
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: X7073755W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.50 (08/30/2007)
          size: 97KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 2201MHz
          capacity: 2201MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
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
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:f0000000-f00fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0100000-f01fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f0704800-f0704bff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0700000-f0703fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:80000000-801fffff memory:80200000-803fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f0300000-f03fffff memory:80400000-805fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:24:ba:51:23
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:2000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:f0200000-f02fffff memory:80600000-807fffff(prefetchable)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 61
                serial: 00:13:e8:dd:a4:2d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.75 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:f0200000-f0201fff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:5000(size=4096) memory:80800000-809fffff memory:80a00000-80bfffff(prefetchable)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0704c00-f0704fff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:f0400000-f04fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:0a:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:16 memory:f0400000-f04007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:0a:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:17 memory:f0400800-f04008ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:0a:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=32
                resources: irq:10 memory:f0400c00-f0400cff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:0a:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:f0401000-f04010ff
           *-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.4
                bus info: pci@0000:0a:01.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:f0401400-f04014ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-U10N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TS05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:1c00(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18e0(size=32) memory:f0704000-f07047ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEKT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXF1A71L9108
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00005956
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 0c46335a-3f79-4266-9565-6c5854c53317
                   size: 296GiB
                   capacity: 296GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-26 01:38:23 filesystem=ext4 lastmountpoint=/2w&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;5&#65533; &#65533;&#65533;:*&#661;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1864; modified=2012-03-17 19:51:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2012-04-22 20:30:41 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 51dc12c0-3dd2-4a6d-957c-1c7411bd3543
                   size: 1881MiB
                   capacity: 1881MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:80c00000-80c000ff ioport:1c20(size=32)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

```

---

### Post by ahallubuntu on 2012-04-22
I've installed probably a dozen Ubuntu servers and/or wired desktop stations and never, ever had the odd ethernet problem you have encountered with this modem.  I have desktop consumer-class hardware that is up 24/7 for months and heavily used - all on Ubuntu 10.04.

There is no generic problem with Ubuntu 10.04 and wired ethernet.

Assuming you have done all updates since your initial install, so you have updated the kernel since your first install of Ubuntu, it's clearly either a specific problem with your modem or a problem with specific hardware in all the computers you are using (are they all exactly the same)?   The solution to the modem problem is simple: install a router behind it.  Problem solved.  My local computer recycling store sells wired routers for $5 used.  You should be able to find a basic wired router that is adequate for about that much money or not much more online.

If I had a "million problems" with Ubuntu 10.04 LTS in the servers I support, I'd never have time to do anything.  Instead, they run trouble-free for months or  even years at a time.  Ubuntu 10.04 is far from perfect, but specific problems unique to some hardware can be addressed individually once, solved, and you move on.

If you would prefer to spend many hours to go install some other operating system over Ubuntu instead of just putting a cheap router there, be my guest.  Since you are using the same kernel modules as Ubuntu, you could have the same ethernet problem with connectivity with this modem that you have with Ubuntu 10.04 .

---

### Post by BobDolman on 2012-04-22
I did some fast research and the conclusion is that Ubuntu 10.04 had some difficulties with some network cards. You should upgrade to 11.04 for a more stable experience. I have multiple OS's running at home, if you inform me what kind of user you are I can suggest you which OS is most suitable for you.

**PS:**
For updating to a newer version you can use the following code: 
- First press "ALT+F2"; you should get an input field.
- Type into the input field: ```
update-manager -d
```

---

### Post by MonkeyPaw on 2012-04-22
Ironically, my last motherboard had connectivity issues on the integrated LAN, but it was only under Windows 7. It was a Realtek LAN, too, so it was a well-supported device. The problem was when I would resume from S3, sometimes it connected, other times it didn't (limited connectivity). I chalked it up to either a buggy LAN device or motherboard. Replaced the motherboard and have never had a problem since. Sometimes you just get a lemon.

---

### Post by ahallubuntu on 2012-04-22
I use 10.04 LTS on my regular laptop but have installed 11.04 on numerous machines.  11.04 is quite good.  The only reason I wouldn't recommend 11.04 is that it's only supported until October of this year, whereas 10.04 LTS is supported until next April at least (since server edition is supported until 2015, I wonder if at least kernel fixes will come through on the desktop version of 10.04?).

I'm probably going to bite the bullet and go for 12.04 LTS once it is released and stable - and see if I can handle Gnome 3...

---

### Post by jesushero on 2012-04-23
Thanks for your replies everyone.

The 6 computers are all entirely different, very different hardware and network cards. So definitely not the same hardware issue.

I've also tried the router approach and this also failed. I also tried a network switch after the modem, but this didn't work either. Weirdly enough, the switch after the modem approach didn't work on Windows either. 

I was thinking of going for a later version, as 10.04 really is the version that started me thinking of moving away from Ubuntu. Up until 8.04 I didn't really have any serious problems, but 8.04 lacks some functionality that I would really like on my laptop. I've still kept two of my computers on 8.04 though, one being a server that I need working with no fiddling about.

Having said that, my Ubuntu servers have mostly been trouble-free. It's the Desktops that I'm having huge problems with. However, because internet is painfully slow in my geographical location, I'm having local mirrors of all repositories for updates and such, and so I need all the computers to run the same OS, preferably also the same version of the same OS, due to finite disk space.

Having full mirrors for the 10.04 and 8.04 repos is already a bit too much for disk space. I also have a local wikipedia mirror and plenty of other databases.

As for what type of user I am:

I use a few servers mainly to support local networking infrastructure with the "essentials" to avoid the slow internet connection as much as possible, backups, file sharing, media projects, IRC chat, etc. 

Then I use a few Desktops for "office stuff", such as emails, web browsing, word processing, latex, gimp, etc. These, I mainly maintain for other people to use. I need these to work out of the box with no fiddling whatsoever. There's nothing extraordinary about these and no reason why they shouldn't just work.

I use a couple of Desktops for studio purposes, audio and video production. I understand this is a bit more complicated, so I can see how it would need a bit of fiddling, but still, Ubuntu Studio 10.04 was a disaster. I had been using 8.04 for a few years and loved it. I am hoping 12.04 will be worth using. My main occupation and income is audio/video production, but I mainly use analog hardware for it, which is good because with the current state of Ubuntu Studio 10.04 I wouldn't be making any money. So currently, I don't even have the studio computers plugged in. I'm waiting for 12.04 to give it another try, and then it's a move to other studio distros if that fails.

I also have a programming and development computer that I don't personally use so much, but it is natural to fiddle with that I guess so no specific issues there.

I realize it would probably be better to use specialized distros for specialized things, such as OpenBSD for servers (which I've used and loved in the past), OpenSuse for office, Debian for programming, and Ubuntu Studio or 64Studio or PureDyne for studio use, but it would really be a pain to keep these updated separately due to crawling internet. I don't have enough disk space to keep repos for all of these. So I have to make do with one distro that fits most of these bills.

This is the IT infrastructure of a small social center that I'm maintaining, so it is stuff that many non-expert users are expected to do high-quality work on, without ever having to look under the bonnet.

So, yes, the 10.04 machines are kept constantly updated.

I get very many complains for things that don't work on the computers, and my list of things to fix is endless. A majority of these problems is stuff that used to work on 8.04 and suddenly doesn't work on 10.04, although the packages are still in the repos. It's astonishing how many packages in the repos are just broken, or they cause the computers to crash or misbehave. CAD software being one primary example that comes to mind. 

I feel that this is a direct result of the six-monthly release cycle, which at times doesn't give enough time for everything to be completed before the release. I thought that LTS releases would not suffer from this as much, but 10.04 does. Which is why I'm considering a move to another distro. Maybe one that focuses more on less but more rigid releases? Maybe also bomb-proof updates?

I've heard good things about Mint, which is Ubuntu based, and someone also mentioned Pinguy OS, which I've not looked into yet. FreeBSD I've used in the past and liked, but wasn't really what I was looking for back then. I don't really know what to do, but I'm hugely disappointed with Ubuntu. I was converted with 6.04, and have used every release (LTS and normal ones) up until 10.04. Things were improving up until 8.04, and went downhill from there.

As for this specific issue, it seems that for some reason the ethernet "carrier" is off by default, as opposed to what goes on with most network hardware, and needs to be "waken up" with something. Windows can do this, but Ubuntu can't. I've no idea what goes on there, as I've never seen this happen before. I've also tried restarting all network hardware. The internet is paid for by someone else, and shared with us. We cannot really ask him to change his network hardware or provider, so our only chance is to make this work somehow.

---

### Post by dandnsmith on 2012-04-23
Looking through this thread, a couple of things registered:

- in the original post there is an IP address 169.254.x.y - which is an unreal address, in that you'll never get it when getting the address from a normal DHCP server - it only happens when there isn't a DHCP offering a proper address, as a kind of fallback (I don't know the full story behind these)

- in the ethernet details I see *RTL8101E/RTL8102E*, which rings a bell - there have been a number of threads with problems networking this family of interfaces (q.v.)

I hope this may help

---

### Post by grahammechanical on 2012-04-23
I use a Thomson TG585 v7

So, I do not agree with the last part of this:

> It seems like the modem, a Thomson TG 585 v7, is not compatible with the networking on this laptop, or incompatible with ubuntu.

I have never had any problem connecting to this modem/router either by ethernet or by wireless since I got it about 3 years ago and I only use Ubuntu.

Regards.

---

### Post by ahallubuntu on 2012-04-23
I wonder if there is some problem on jesushero's network?  One flaky piece of network hardware - one misconfigured switch, one malfunctioning NIC on one desktop machine - could cause issues on the whole network.  I guess I'd ask how the whole network is setup?  If a router behind the modem does not improve the situation, I wonder if the modem is really the problem at all - but it depends exactly how the network is setup.  Does the modem or a router do DHCP or do you use static IP?

jesushero, is it possible to isolate your network and have say just one desktop connected at a time?  Do you have the same sort of problems with just one desktop connected to your modem?

---

### Post by jesushero on 2012-04-23
> **ahallubuntu said:**
> I wonder if there is some problem on jesushero's network?  One flaky piece of network hardware - one misconfigured switch, one malfunctioning NIC on one desktop machine - could cause issues on the whole network.  I guess I'd ask how the whole network is setup?  If a router behind the modem does not improve the situation, I wonder if the modem is really the problem at all - but it depends exactly how the network is setup.  Does the modem or a router do DHCP or do you use static IP?

jesushero, is it possible to isolate your network and have say just one desktop connected at a time?  Do you have the same sort of problems with just one desktop connected to your modem?

Originally 5 computers were networked together using a static IP and a 5 port network switch. This was just a LAN, with no internet. Then the internet sharing idea came up, so we initially tried disconnecting one of the computers from the switch and plugged in the Thomson thingie instead. It didn't work, so I disconnected the laptop from the LAN (the laptop being the main computer I want internet on to start with), and connected the laptop directly to the Thomson via ethernet.

This didn't work either, so I disconnected one desktop computer from the LAN and connected it directly to the Thomson via ethernet. It didn't work, so we brought in a random windows laptop and it worked instantly. Then we disconnected everything from the switch, and plugged in just the thomson and the windows laptop. We powered the switch and the router off, and then back on, just in case. The switch is a dead simple one, nothing there to set. It didn't work. So the windows laptop only works directly connected to the Thomson, and will not work via the switch. The Ubuntu laptops don't work at all, no matter what you do. It doesn't make any difference if there is an entire LAN or just one computer connected directly to the Thomson.

So, the ethernet cable itself works, as it works on at least one computer. The switch works on the LAN, but on nothing else, so I'm leaving it out for now, until I can at least get one of my ubuntu computers to work. So for now, I'm just trying to figure it out with one computer connected directly to the thomson. 

The DHCP transaction times out for some reason. It times out in far more time than it takes the windows laptop to get an IP, which is less than a second. Which is why the weird IP is assigned as a fallback. Pinging doesn't work, static IP doesn't work (the Thomson probably doesn't support it, as it is set to DHCP), and the nm-tool output tells me there's no carrier. While just on the LAN, the nm-tool tells me that the carrier is on. As soon as the LAN cable is plugged out, the nm-tool tells me that the carrier is off. This does not change back to on when plugging in the Thomson cable. It only changes back to on when plugging in the LAN cable. The laptop has eth0 as the DHCP device and eth1 as the static device for the LAN. The DHCP on eth0 has worked on other wired networks in the past with no issues. DHCP on wifi works, on the same Thomson, but the wifi between this laptop and the thomson keeps on dropping the connection. No network connection is set to auto, I usually manually connect via the nm-applet icon. I've also tried the ifconfig method on the terminal, on both laptop and desktop, but no luck. DHCP just times out and it seems like there's nothing in the other end of the ethernet cable.

I hope this makes it clearer. Thanks.

---

### Post by dandnsmith on 2012-04-23
I'm now wondering if the switch detail is the problem. What make and model are the switch?
I do use a hub, rather than a switch - just because that was what I originally bought - but it may have saved me from this particular problem.

The other thing is the comment about the cable "So, the ethernet cable itself works, as it works on at least one computer."
A couple of days ago I was trying to work out why an ethernet cable which successfully connected one PC to a hub didn't work when a different PC was plugged in instead. To get the second to work I had to swap the cable for another (which worked for either PC). I don't yet know whether it's a connection problem (poor contact in the socket) or one of them is a x-over cable, but not the other.

---

### Post by ahallubuntu on 2012-04-23
Have you tried putting a router (not a switch or a hub) behind the Thomson modem?  If you use a switch or a hub, the modem is still doing the DHCP and controlling the network.  If there is some incompatibility between Ubuntu and this device, putting a router in there to isolate the local network from the modem might solve your problem.  (Then set the subnet of the router to be different from the one the modem is using - that is, if the modem uses 192.168.0.1 make sure the router uses 192.168.1.1 as its gateway/subnet.)

Do check the crossover vs. patch able idea as well.  Some clients can automatically do a crossover without a crossover cable.  I've seen modems designed to be attached to a client using a crossover cable, though I'm not familiar with the Thomson.

---

### Post by jesushero on 2012-04-23
The cable is definitely not a crossover cable, as I've made it myself. I don't have a crossover cable here.

The switch is a no-name.. No idea. But it doesn't work even when the switch is out of the way. 

Mmmm.. No actually, I haven't tried a router behind the modem. I don't have a router. I only have a hub and a switch that doesn't work with this modem. Haven't tried the hub out yet.. Maybe I should?

The thomson uses a normal ethernet, not a crossover.

---

### Post by dandnsmith on 2012-04-24
I've been thinking about what has been said so far.

In the initial post you mentioned having tried a number of computers with linux installed and had it fail for all.

I then started wondering about whether it is something common in the way you have them set up which is causing the problem, so can I suggest that you try booting from a LiveCD to see whether things work that way (probably starting with a wired setup is the most straightforward).

If that works, then we can take it from there.

---

### Post by jesushero on 2012-04-24
> **dandnsmith said:**
> I've been thinking about what has been said so far.

In the initial post you mentioned having tried a number of computers with linux installed and had it fail for all.

I then started wondering about whether it is something common in the way you have them set up which is causing the problem, so can I suggest that you try booting from a LiveCD to see whether things work that way (probably starting with a wired setup is the most straightforward).

If that works, then we can take it from there.

Good idea, I'll get a live CD and try it out. I'll post back soon.

---

### Post by jesushero on 2012-04-25
Ok, haven't tried a live CD out yet, I've been trying to download one.. But in the meantime, I've tried something else quite interesting. 

I've managed to connect to the wired network using an Acer netbook running Ubuntu 10.04. It did it instantly, no set up required. The same netbook is also able to connect to the WiFi of the same modem without the disconnection problems of the Toshiba. 

So now I've started a WiFi sharing point from the Acer, and I've connected the Toshiba to the Acer, and I've got internet on the Toshiba without problems. Obviously this is quite a ridiculous setup, but it demonstrates that Ubuntu is capable of connecting to this network, both wired and wireless, on at least one computer. 

So I've now deduced the problem areas to the following possibilities:

1) The six different network cards on the six different computers I have here just so happen to all be incompatible with the Thomson modem.

2) The drivers that come with the Kernel are not good enough for the six specific network cards, but works on others.

3) The way Ubuntu uses the kernel drivers is problematic for these six network cards, but works on others.

4) Considering that the Thomson modem and the Acer laptop are all very recent devices, while all six computers that don't work are at least 5 years old, or older, could it be that newer network devices use some kind of new communication mode, that is not compatible with older hardware? This kind of goes with 1 I guess..


I'm now downloading several live CD's of several versions of Ubuntu, and also other OS's and I'll proceed to test if the toshiba works with any of these. The one it works with is the one I'll be using. If it doesn't work with any of these, I guess some sort of router would solve the problem, by isolating the modem from the Toshiba and other computers, and acting as an interface that the LAN can recognize, while at the same time being able to communicate with the Thomson.

But how would I know if a router would work with the Thomson, and with the LAN, before buying it?

Any other ideas?

---

### Post by ahallubuntu on 2012-04-25
Where I live, I can buy a used router (wired) for $5 USD at a local thrift store.  I don't know if you are so lucky - but for that price it's not worth worrying about, really.  A wired and especially a wireless router is handy to have around as a spare, anyway.  Do you have a Craigslist near you that sells a variety of computer equipment?

Can you borrow a router to try to satisfy your need to know whether it will fix your problem or not before buying one?

It's also possible there is some setting in the Thomson that is causing issues with your Ubuntu desktops.  You might also see if the manufacturer offers a newer firmware for the Thomson - sometimes that can fix compatibility issues.

---

### Post by dandnsmith on 2012-04-26
> **jesushero said:**
> But how would I know if a router would work with the Thomson, and with the LAN, before buying it?


After your tale of woe so far, I'd say all bets were off - it's going to be 'suck it and see'.

Personally, I'd go with the LiveCD tests first, just to see what that throws up.

---

