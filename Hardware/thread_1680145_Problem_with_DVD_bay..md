---
title: "Problem with DVD bay."
date: 2011-02-02
forum: Hardware
---

### Post by commbba on 2011-02-02
Hello my friends.
First of all I'm having an Acer F3000 laptop with 1.86 AMD cpu,1.2 GB ram,DVD-rw,60 GB HDD,124 Mb GPU and I'm having the following problem.
The system don't recognises the CD-DVD disks,mine or the commercial ones.
I'm doing clean install every new release,because the new packages,in my computer,doesn't work fine with the old ones,so I have to write the .iso disk at a computer shop.The problem is not the isntalling process and I'm very satisfied with Ubuntu,but I'm thinking off changing OS,with something in KDE or another distro of linux,to make DVD bay work.
Do you think that will be possible ?Passing to KDE may mount the DVD bay ?All these happened after the update of Feisty,till Feisty I could saw DVD movies with VLC very good.
Neither I can write disks and I have installed many recording programs and all show me malfunction messages.
Times to times I'm trying to find a solution but with no use,so I decided to ask about the change of OS.Have you ever faced a problem like that and found a solution with another OS ?
Thank you for your answers.

---

### Post by ronnielsen1 on 2011-02-02
I don't think KDE would matter at all. The only times I've seen a cd/dvd drive not work is either a bad unit or a memorex. Can you post the output of [COLOR=Blue]**sudo lshw **[/COLOR]from a terminal?

---

### Post by commbba on 2011-02-02
aby@aby:~$ sudo lshw
[sudo] password for aby: 
aby                       
    description: Notebook
    product: Ferrari 3000
    vendor: Acer
    version: 0
    serial: LXFR105006347028FEEF00
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook uuid=20B28F61-E00E-D811-A58B-00C09F2FCA64
  *-core
       description: Motherboard
       product: Aspire 1450
       vendor: Acer,Inc.
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A20 (10/29/2003)
          size: 115KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppy1200 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: U23
          size: 928MHz
          capacity: 928MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: M3
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:d0100000-d01fffff memory:d8000000-dfffffff
           *-display
                description: VGA compatible controller
                product: M9+ 5C61 [Radeon Mobility 9200 (AGP)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:4 memory:d8000000-dfffffff ioport:9000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:5 memory:58000000-58000fff ioport:2000(size=256) ioport:2400(size=256) memory:50000000-53ffffff memory:54000000-57ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:5 memory:d0006000-d00067ff memory:d0000000-d0003fff
        *-network:0
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:11 memory:d0004000-d0005fff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:4 ioport:1c00(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:5 ioport:1c20(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:9 ioport:1c40(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:d0006800-d00068ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:4 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c60(size=16)
           *-disk
                description: ATA Disk
                product: IC25N060ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO3O
                serial: MRG309K3GVENWK
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000a00ce
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: dea40134-3b03-487a-870f-9035973e3f97
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-15 16:53:16 filesystem=ext4 lastmountpoint=/1&#65533;&#65533;J&#65533;m&#65533;hJW&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;q!&#65533;hJW&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;m&#65533; &#65533;8&#65533;&#65533;It!&#65533;&#65533;j modified=2011-01-29 08:46:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-02-02 07:08:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2380MiB
                   capacity: 2380MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2380MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r
                configuration: status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:9 ioport:1000(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:9 ioport:1400(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:c0:9f:2f:ca:64
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.2 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:4 ioport:1800(size=256) memory:d0006c00-d0006cff
     *-scsi
          physical id: 1
          bus info: usb@4:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Flash R/W
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 2002
             serial: ST7265-2002
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:6b:48:38:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-25-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
aby@aby:~$

---

### Post by ronnielsen1 on 2011-02-03
I don't know. I'm sorry. I was hoping someone else posted

---

