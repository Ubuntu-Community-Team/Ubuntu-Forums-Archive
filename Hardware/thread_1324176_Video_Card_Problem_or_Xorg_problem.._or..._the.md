---
title: "Video Card Problem or Xorg problem.. or...? the"
date: 2009-11-12
forum: Hardware
---

### Post by Tony Ricena on 2009-11-12
I've been having problems with my system (well they are problems that shouldn't be happening imo).

Whenever I try to record my desktop with Desktop effects enabled using gtk-recordmydesktop i get little to no performance aka it completely lags.  The only way to work around this is to disable all desktop effects which is not what I want.  

Also when i remote into the system using remote desktop viewer (vnc) I only get a "Screenshot" where nothing I do shows up on the computer I am remoting from.  Once again the other way to work around is to disable desktop effects.  

I know this may be trivial to most, but its a concern for me.  The funny thing is my laptop that is running Ubuntu 9.04 Jauntry works perfectly fine (desktop effects enabled and both programs work with no problem at all).  

I may have narrowed down the problem to xorg but I'm not completely sure.

On my desktop i am using:
9.04 Jauntry Ubuntu i386
All xorg is up to date

Hardware:
ATI Radeon HD 4650 (using the proprietary driver from ATI download Catalyst 9.10.. tried to use the driver ubuntu wants me to use but its a poor performance when playing back dvd's etc)

Its a new system running a AMD Phenom II X3 2.80ghz Black Edition CPU
4Gb 1066mhz memory

When I had Windows 7 installed on this system, everything was brilliant and working top notch.  When I put Ubuntu on it, these things worked like crap.  

I have gone through the whole editing the xorg.conf file doing a number of things (such as disabling 3d acceleration at least if I read correctly I did) and a number of other things to try and get this system's video to work at peak performance but no success.  If you need more information, please let me know.  

I would really appreciate some help on this cause its driving me nuts!  All this equipment on the system is for high performance so I want it to work as it should.  thank you

---

### Post by Tony Ricena on 2009-11-12
Bump.. Please anything to help me

---

### Post by Tony Ricena on 2009-11-12
here is my lshw
```
 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             physical id: 1
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 2
             slot: A2
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 3
             slot: A3
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.2
          size: 2800MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:2
          physical id: 2
          bus info: cpu@2
          version: 15.4.2
          size: 2800MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:e000(size=4096) memory:fde00000-fdefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV730 PRO [Radeon HD 4650]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:fdee0000-fdeeffff ioport:ee00(size=256) memory:fde00000-fde1ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: R700 Audio Device [Radeon HD 4000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fdefc000-fdefffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port A)
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 AHCI Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: scsi4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list emulated
                configuration: driver=ahci latency=0
                resources: irq:16 memory:fddfe000-fddfffff
              *-disk
                   description: ATA Disk
                   product: ST31500341AS
                   vendor: Seagate
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sda
                   version: CC1H
                   serial: 9VS1B2NZ
                   size: 1397GiB (1500GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=00000001
                 *-volume:0
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@4:0.0.0,1
                      logical name: /dev/sda1
                      logical name: /
                      version: 1.0
                      serial: b48340e6-e5a8-43e0-9355-d019277cf6ac
                      size: 1387GiB
                      capacity: 1387GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                      configuration: created=2009-11-12 11:14:31 filesystem=ext4 lastmountpoint=/Q.&#65533;&#65533;7&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#1821;&#65533;&#65533;9&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;0)&&#65533;&#65533;( modified=2009-11-12 18:37:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-12 19:39:49 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: scsi@4:0.0.0,2
                      logical name: /dev/sda2
                      size: 9593MiB
                      capacity: 9593MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sda5
                         capacity: 9593MiB
                         capabilities: nofs
           *-ide
                description: IDE interface
                product: JMB362/JMB363 AHCI Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:df00(size=8) ioport:de00(size=4) ioport:dd00(size=8) ioport:dc00(size=4) ioport:db00(size=16)
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:c000(size=4096) memory:fd900000-fd9fffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:24:1d:74:00:08
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:28 ioport:ce00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:fdf00000-fdf0ffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02e000-fe02efff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02d000-fe02dfff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02c000-fe02c0ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02b000-fe02bfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02a000-fe02afff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fe029000-fe0290ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi6
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=32
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
           *-cdrom:0
                description: DVD-RAM writer
                product: DVD RW DRU-820A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0b
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM SD-616Q
                vendor: SAMSUNG
                physical id: 0.1.0
                bus info: scsi@6:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: F401
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fe024000-fe027fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
             resources: ioport:b000(size=4096) memory:fdb00000-fdbfffff memory:fda00000-fdafffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:04:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:fdbff000-fdbff7ff memory:fdbf8000-fdbfbfff
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe028000-fe028fff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 3
          bus info: usb@1:1
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C5500
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdb

```

---

