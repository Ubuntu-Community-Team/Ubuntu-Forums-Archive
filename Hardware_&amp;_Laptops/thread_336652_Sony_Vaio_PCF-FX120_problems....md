---
title: "Sony Vaio PCF-FX120 problems..."
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by gironja on 2007-01-11
###
Edit: Title should read "PCG-FX120" instead of PCF-FX120".
###

Hi!

My GF have a PCG-FX120 Laptop, and it was running Dapper (alternate, and GNOME desktop) since it's released, and it worked good (not awesome since the lap. specs are quite old...). But now it was kind of slow compared to when it was installed (yes... that's is kind of obvious...). Since I'm running Edgy in my Lap, I decided to run it on her's. But a few problems were encountered.

1. It's memory (190MB as of "lshw" command) is getting full since it's login. I must mention that I first used Edgy normal DVD, and then the Alternate, since that last is for PCs with about 128MB.

2. The Splash Screen is VERRRY fuzzy: all I can see is white lines inside a black square in the center of the screen, at boot-up and at shutdown. 

3. All the progress bars, instead of the normal orange, they appear like "transparent white"... what I thought may be video driver problems.

I installed XFCE desktop and switched from GNOME to XFCE and the use of memory now is lower, but I think it may be high, since I measure it without anything running (only what the OS loads at start up). In GNOME, the system monitor showed 70-72% in Programs and 20-25% Cache aproximately (in the system monitor on the GNOME panel). In XFCE the use was in about 55% and 18% SWAP. 

I will now start compiling the 2.6.19 kernel, to see if I can gain some "speed" and/or performance, but I don't know if it will solve my problems at all (at least the memory one). 

Now the questions :D

Is there a GRUB switch that can fix the Splash visualizations? Is there any way to get my video driver working correctly? What can I do to solve the excessive RAM consumption?
 
The PC Specs are:

```

soli@solilap:~$ sudo lshw
Password:
solilap                   
    description: Notebook
    product: PCG-FX120(UC)
    vendor: Sony Corporation
    version: N/A
    serial: 28318330-3601061
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: WXP03U0 (04/12/02  )
          size: 114KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ieee1394boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.8.6
          slot: N/A
          size: 700MHz
          capacity: 700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1Cache
             size: 32KB
             capabilities: asynchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2Cache
             size: 256KB
             capacity: 256KB
             capabilities: burst external write-back data
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 192MB
          capacity: 512MB
        *-bank:0
             description: SODIMM SDRAM Synchronous 100 MHz (10.0 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM1
             size: 128MB
             width: 32 bits
             clock: 100MHz (10ns)
        *-bank:1
             description: SODIMM SDRAM Synchronous 100 MHz (10.0 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM2
             size: 64MB
             width: 32 bits
             clock: 100MHz (10ns)
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 11
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:f8000000-fbffffff iomemory:f4000000-f407ffff irq:9
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:f4101000-f41017ff iomemory:f4104000-f4107fff irq:9
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 2
                bus info: pci@01:02.0
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f4102000-f4102fff iomemory:b00502010-b0050200f irq:9
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 2.1
                bus info: pci@01:02.1
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f4103000-f4103fff iomemory:b00906010-b0090600f irq:9
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 03
                serial: 08:00:46:13:51:0d
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.2.3 link=yes multicast=yes port=MII speed=100MB/s
                resources: iomemory:f4100000-f4100fff ioport:3000-303f irq:9
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1800-180f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHM2100AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3822
                   serial: 01010701
                   size: 9590MB
                   capacity: 9590MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux swap / Solaris partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 956MB
                      capabilities: primary nofs
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 8628MB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-C2402
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1521
                   serial: y000503668
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:1810-181f irq:9
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:2400-241f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:1840-187f irq:9
        *-communication UNCLAIMED
             description: Modem
             product: 82801BA/BAM AC'97 Modem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             resources: ioport:2000-20ff ioport:1880-18ff irq:9
     *-usb:0
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@06:00.0
          version: 61
          width: 32 bits
          clock: 33MHz
          capabilities: uhci bus_master cap_list
          configuration: driver=uhci_hcd
          resources: iomemory:16000800-160008ff ioport:3c80-3c9f irq:9
        *-usbhost
             product: UHCI Host Controller
             vendor: Linux 2.6.17-10-generic uhci_hcd
             physical id: 1
             bus info: usb@3
             logical name: usb3
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 0.1
          bus info: pci@06:00.1
          version: 61
          width: 32 bits
          clock: 33MHz
          capabilities: uhci bus_master cap_list
          configuration: driver=uhci_hcd
          resources: iomemory:16000900-160009ff ioport:3ca0-3cbf irq:9
        *-usbhost
             product: UHCI Host Controller
             vendor: Linux 2.6.17-10-generic uhci_hcd
             physical id: 1
             bus info: usb@4
             logical name: usb4
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: VIA Technologies, Inc.
          physical id: 0.2
          bus info: pci@06:00.2
          version: 63
          width: 32 bits
          clock: 33MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:16000a00-16000aff iomemory:16000b00-16000bff irq:9
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.17-10-generic ehci_hcd
             physical id: 1
             bus info: usb@5
             logical name: usb5
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
           *-usb
                description: Mass storage device
                product: USB2.0 Storage Device
                vendor: DMI
                physical id: 1
                bus info: usb@5:1
                logical name: scsi1
                version: 0.01
                serial: 200604217698
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s
              *-disk
                   description: SCSI Disk
                   product: 0A
                   vendor: ST325082
                   physical id: 0.0.0
                   bus info: scsi@1:0.0.0
                   logical name: /dev/sdb
                   version: 0000
                   size: 232GB
                   capabilities: partitioned partitioned:dos
                 *-volume
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: scsi@1:0.0.0,1
                      logical name: /dev/sdb1
                      capacity: 232GB
                      capabilities: primary
     *-firewire
          description: FireWire (IEEE 1394)
          product: IEEE 1394 Host Controller
          vendor: VIA Technologies, Inc.
          physical id: 0.3
          bus info: pci@06:00.3
          version: 46
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci1394
          resources: iomemory:16000000-160007ff ioport:3c00-3c7f irq:9
soli@solilap:~$ 


```

Sorry for its lenght... I just wanted to give the most information I could, so you guys can better help me.

Thanks!


jNa

---

### Post by jarviw on 2007-02-09
I am also using this machine.  pretty amazed how it is still running.

I have installed dapper on this guy since dapper is out, and now I am using edgy (ubuntu).  
honestly, it's not the fastest machine in the world, but it runs smoothly for everyday web browsing and others.  I like it so much I actually have this computer on 24/7, as "the computer to use".

well... to be fair, I should also mention that I have 512 MB of RAM and a new 40G HD.
I normally run at about 180MB RAM used.

that said, I suggest you go dig eBay for some old RAM.  they are actually all over the place, as most P3 notebooks are retired by now.  (I can give you my 64MB, but it's not going to help you)
otherwise, frankly, I don't think ubuntu (xubuntu) were designed to revive legacy hardwares anymore.  you should try other distros, like Zenwalk, or KateOS.

good luck!

---

