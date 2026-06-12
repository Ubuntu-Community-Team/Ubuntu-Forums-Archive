---
title: "Shuttle MV17 Motherboard issues.. Help needed!"
date: 2008-11-20
forum: Hardware
---

### Post by jesushero on 2008-11-20
I am running a small server on a recycled computer I put together from different parts. The motherboard seems to be a Shuttle MV17 (or similar), with the VIA VT8605 chipset. However, it only has a single PCI slot, since it is fitted in a weird case. It has onboard VGA with composite output, Ethernet and sound. It's a small one, probably Micro or Mini ATX.

Looks exactly like this: [http://www.acesuppliers.com/Supplier_Company/ENDAT-3701_Product_Showroom_12679.html](http://www.acesuppliers.com/Supplier_Company/ENDAT-3701_Product_Showroom_12679.html)

The processor is an intel celeron 800mhz, 100mhz clock.

The ram is a no-name 128mb, PC133 (133mhz clock).

I am having some occasional crashes and ran memtest86+ which came up with an error in the first pass.

I've googled quite a bit but didn't find the exact same motherboard I have, or any tech details of it. First of all, I think the Shuttle MV17 is supposed to be an 133mhz FSB board. However, one silly-looking website said that it's compatible with Celeron and PIII processors with FSB's from 66mhz to 133mhz, including 100mhz. Can a 133mhz FSB board be compatible with a 100mhz processor? What would happen if it wasn't compatible?

The ram supposedly HAS to be at 133mhz. Can a 133mhz ram be compatible with a 100mhz FSB? It's an SDRAM. The ratio would be quite weird, unless I'm doing the maths totally wrong.

The thing is, the server used to run fine since June, NONSTOP!!! Lately I've had a power-cut and when it powered back up again, it wouldn't boot. I restarted a couple of times and it finally did boot but only found 50mb of ram. Then I rebooted and was fine again, seeing all 128mb. I then ran the memtest that found the error. I've recently added heavier stuff on there, such as an SVN repository. It sometimes crashes during massive checkouts or exports. It's usually fine with a reboot, but I'd like to locate the problem.

Can someone please shed some light? 

OS: Ubuntu Server 8.04.1

lshw output (in case you have some free time):
```
the-server               
    description: Desktop Computer
    product: VT8605
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8605-686A
       vendor: Shuttle Inc.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (08/21/2001)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: Socket 370
          size: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 128KiB
     *-cache
          description: L2 cache
          physical id: a
          slot: External Cache
          size: 128KiB
          capacity: 2MiB
          capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 1e
          slot: System board or motherboard
          size: 128MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 128MiB
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: BANK_1
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: BANK_2
     *-pci
          description: Host bridge
          product: VT8605 [ProSavage PM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT8605 [PM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ProSavage PM133
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: driver=prosavage_smbus latency=248 maxlatency=255 mingnt=4 module=i2c_prosavage
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: ST3120026A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.06
                serial: {serial-here}
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature={sig-here}
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: {serial-here}
                   size: 110GiB
                   capacity: 110GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-28 23:07:03 filesystem=ext3 modified=2008-11-20 02:22:26 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-20 02:22:26 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: {serial-here}
                   size: 980MiB
                   capacity: 980MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth0
             version: 10
             serial: {serial-here}
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip={ip-here} latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW323
             vendor: Agere Systems
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394

```

---

