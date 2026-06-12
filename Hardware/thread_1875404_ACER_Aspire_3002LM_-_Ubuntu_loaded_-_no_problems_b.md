---
title: "ACER Aspire 3002LM - Ubuntu loaded - no problems but slow"
date: 2011-11-04
forum: Hardware
---

### Post by gcmelzi on 2011-11-04
Hello everybody. 
I'm looking for any tip helping me addressing this problem: I loaded Ubuntu (currently 11.04) on my son's laptop (an old ACER Aspire 3002LM): it took a while but no problems were reported and the system is up and working. Via Ndiswrapper I got the Wlan working as well (not stable) but the point is the system looks terribly slow.
I spent some time on Google and Forums: most of the threads are about WiFi and screen resolution. There are some discussions about the sis card and its support: I'm not sure I understood them well, but I can ensure the xserver-xorg-video-sis package is installed and the sisfb module is added in /etc/modules. 
I just wonder if anyone can suggest a direction for improving performances. 
The other son is running kubuntu on an Aspire 3614WLMi more then decently.

See below output for lshw:
```
simo-aspire-3000
    description: Computer
    version: Not Applicable
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=C01467B6-63B0-D911-B4D9-00C09F94CFB0
  *-core
       description: Motherboard
       product: Lugano M
       vendor: Acer, Inc.
       physical id: 0
       version: Not Applicable
       serial: LXA550504651709B1AEM00
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A18
          date: 04/12/05
          size: 101KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 2800+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          slot: Socket A
          size: 800MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 CACHE
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 10
          slot: System board or motherboard
     *-memory:1 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM DDR Synchronous
             physical id: 0
             slot: DIMM1
             size: 256MiB
             width: 64 bits
     *-memory:2 UNCLAIMED
          physical id: 2
        *-bank UNCLAIMED
             description: DIMM DDR Synchronous
             physical id: 0
             slot: DIMM2
             size: 256MiB
             width: 64 bits
     *-memory:3 UNCLAIMED
          physical id: 3
     *-memory:4 UNCLAIMED
          physical id: 5
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=64
          resources: irq:0 memory:e0000000-e1ffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:a000(size=4096) memory:e2100000-e21fffff memory:e8000000-efffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:a000(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:8100(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2000(size=16)
           *-disk
                description: ATA Disk
                product: IC25N060ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO3O
                serial: MRA301KEKKMPHH
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00068290
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b705c7a2-8364-4e4b-8672-0190830ee3f9
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-02 12:11:13 filesystem=ext4 lastmountpoint=/ modified=2011-09-02 12:53:58 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-09-06 11:56:44 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 445MiB
                   capacity: 445MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 445MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD-RW DVR-K15RA
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:1000(size=256) ioport:1c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:1400(size=256) ioport:1c80(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:e2000000-e2000fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:e2001000-e2001fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:e2002000-e2002fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:c0:9f:94:cf:b0
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 ioport:1800(size=256) memory:e2003000-e2003fff memory:28000000-2801ffff
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:19 memory:28020000-28020fff ioport:2400(size=256) ioport:2800(size=256) memory:20000000-23ffffff memory:24000000-27ffffff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:08:35:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wlanutg driverversion=1.56+Roper,03/14/2005,7.2.0.40 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11g
```
and from lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

Thanks for anything you can suggest

---

