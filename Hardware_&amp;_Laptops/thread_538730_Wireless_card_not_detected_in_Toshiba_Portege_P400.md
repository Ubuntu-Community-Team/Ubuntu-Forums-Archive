---
title: "Wireless card not detected in Toshiba Portege P4000 Laptop with XUbuntu"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by sysiphean on 2007-08-30
I have a fairly old Toshiba Portege laptop, model P4000 and I am trying to get my wireless card working with xubuntu. I was previously using mandrake, and I was able to get the wireless card working.

Despite following the wireless troubleshooting guide, I didn't get as far as persuading xubuntu to recognise the device. It doesn't show up if I do a lshw, lspci, lsusb or sudo pccardctl ident. However, if I try

sudo pccardctl status 0
I get
3.3V 16-bit PC Card

Which I'm guessing could be the card. I have no idea how to configure this manually however. From what I've read about my laptop, the wireless card is a PCMCIA device, and recall that in Mandrake I was using the orinoco module, but I didn't need to set it up myself in mandrake. I tried creating my own /etc/pcmcia/config.opts file with some values I found on the web, but these didn't work

device "orinoco_cs'
  class "network" module "orinoco_cs"

card "TOSHIBA Wireless LAN Card"
  #version "TOSHIBA", "Wireless LAN Card"
  manfid 0x0156, 0x0002
  bind "orinoco_cs"

... gives me
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No Such Device

So I suppose thet the manfid address range is wrong, but how am I supposed to figure it out?


The troubleshooter simply says that if the pccardctl ident fails, then the memory cannot be read from the device. Is this the end of the road? What info can I post to help shed some light on this situation?

Thanks in advance

sudo lshw

    description: Notebook
    product: P4000
    vendor: TOSHIBA
    version: PP400E-0008L-EN
    serial: 91369533G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=user-requested chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=A5A47680-AF24-11D5-8000-B0D091369533
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: 0000000000
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.30 (08/24/2001)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.10
          slot: IC3
          size: 750MHz
          capacity: 750MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 32KB
             capacity: 32KB
             clock: 1GHz (1ns)
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 256KB
             capacity: 256KB
             clock: 1GHz (1ns)
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 128MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 128MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: M1644/M1644T Northbridge+Trident
          vendor: ALi Corporation
          physical id: f0000000
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f0000000-f3ffffff
        *-pci
             description: PCI bridge
             product: PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: CyberBlade XPAi1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@01:00.0
                version: 82
                size: 32MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fc000000-fdffffff iomemory:fbc00000-fbffffff iomemory:f8000000-f9ffffff iomemory:f7ff8000-f7ffffff irq:11
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:f7eff000-f7efffff irq:11
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-23-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: DataTravelerMini
                   vendor: Kingston
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   serial: 5B7218690952
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=200mA speed=12.0MB/s
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: c3
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE
             resources: ioport:eff0-efff irq:255
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHK2060AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: D834
                   serial: 01108879
                   size: 5729MB
                   capacity: 5729MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 3106MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 2619MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-C2502
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1313
                   serial: 9100105426
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451
             resources: ioport:1000-10ff iomemory:2c100000-2c100fff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: M1533 PCI to ISA Bridge [Aladdin IV]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus
        *-network
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 08
             serial: 00:00:39:4c:51:9a
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A ip=192.168.2.5 link=no multicast=yes port=MII speed=10MB/s
             resources: iomemory:f7efe000-f7efefff ioport:eec0-eeff iomemory:f7d00000-f7dfffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 10
             bus info: pci@00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:2c101000-2c101fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: ToPIC100 PCI to Cardbus Bridge with ZV Support
             vendor: Toshiba America Info Systems
             physical id: 11
             bus info: pci@00:11.0
             version: 32
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:2c102000-2c102fff irq:11
        *-pcmcia:2
             description: CardBus bridge
             product: ToPIC100 PCI to Cardbus Bridge with ZV Support
             vendor: Toshiba America Info Systems
             physical id: 11.1
             bus info: pci@00:11.1
             version: 32
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:2c103000-2c103fff irq:11
        *-system UNCLAIMED
             description: System peripheral
             product: SD TypA Controller
             vendor: Toshiba America Info Systems
             physical id: 12
             bus info: pci@00:12.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:2c104000-2c1041ff irq:255
  *-battery
       description: Lithium Ion Battery
       product: LI615A
       vendor: TOSHIBA
       physical id: 1
       version: 08/30/01
       serial: 1000007640
       slot: 1st Battery
       configuration: voltage=10.8V
  *-scsi
       physical id: 2
       bus info: scsi@1
       logical name: scsi1
       capabilities: scsi-host
       configuration: driver=usb-storage


uname -s -r -v -m
Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686

---

