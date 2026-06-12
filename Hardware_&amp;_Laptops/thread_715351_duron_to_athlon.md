---
title: "duron to athlon"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by NULL712 on 2008-03-04
OK here is my problem I have a mainboard from a compaq and it has a 700MHz Duron in it. I got a hold of an Athlon and I droped the little guy into my comp. When I try to boot all I get is the Compaq splash screen. I found the board in a mutilated compaq case on the side of the street son I don't know what model the comp was. So I am stuck with my Duron and stuck with crap performance.

ubuntu 7.10, 630.4Mb PC133 SDRAM, ATI Radeon 7500 

any ideas I would like some sort of performance boost but keep in mind that this comp is a project comp and the whole idea is to use free unwanted parts, so i can't buy any thing for it. 

this is th print from lshw  |
                                     \/
                        
go-green-01               
    description: Mini Tower Computer
    product: Compaq PC
    vendor: Compaq
    version: N/A
    serial: 3333333333333333
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower
  *-core
       description: Motherboard
       product: 06E4h
       vendor: Compaq
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 786K1 (09/14/2000)
          size: 64KB
          capacity: 192KB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Duron(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.3.0
          slot: U12A
          size: 750MHz
          capacity: 1250MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             size: 1KB
             capacity: 512KB
             capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 640MB
          capacity: 1536MB
        *-bank:0
             description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: DIMM1
             size: 256MB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
             physical id: 1
             slot: DIMM2
             size: 256MB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:2
             description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
             physical id: 2
             slot: DIMM3
             size: 128MB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-pci
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon RV200 QW [Radeon 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-network
             description: Ethernet interface
             product: SMC2-1211TX
             vendor: Accton Technology Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             logical name: eth0
             version: 10
             serial: 00:10:b5:84:18:13
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.45 latency=66 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-multimedia:0
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=cx8800 latency=66 maxlatency=55 mingnt=20 module=cx8800
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=64 module=via82cxxx
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC AC420400D
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: J58OA30K
                   serial: WD-WT6620085552
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 18GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 855MB
                      capacity: 855MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 854MB
                         capabilities: nofs
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=66 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia:1
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
     *-scsi
          physical id: 1
          bus info: usb@2:1.1
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: IntelligentStick
             vendor: I-Stick2
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2.00
             size: 121MB
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sda
                size: 121MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   logical name: /dev/sda1
                   capacity: 117MB
                   capabilities: primary bootable

---

### Post by overdrank on 2008-03-04
Hi and from my experience you may have to change some jumpers on the motherboard to use the athlon. If you can find the model of the motherboard you should be able to download the manual.

---

### Post by NULL712 on 2008-03-05
Thanx for the quick reply! I have been having issues trying to find the model of the mobo but from what I can tell by doing google searches it's a FIC UWAVE.

---

