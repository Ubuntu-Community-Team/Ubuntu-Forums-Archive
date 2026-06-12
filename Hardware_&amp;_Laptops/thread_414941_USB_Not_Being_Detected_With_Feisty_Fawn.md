---
title: "USB Not Being Detected With Feisty Fawn"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by sankarj12 on 2007-04-20
When I have installed Feisty Fawn, I noticed that my wireless USB adapter was not warm (it usually is with past versions).  I tried to use ndiswrapper, but all that it said was "driver present", not "hardware present".  When I plugged in a flash drive, nothing showed up.  I concluded that Feisty Fawn did not detect my USB, which is in the motherboard.  Is there anything I can do to get it detected?  Remember that it was detected in Edgy Eft and Dapper Drake.

---

### Post by Jussi Kukkonen on 2007-04-20
```
sudo lsusb -vv
sudo lshw
dmesg | grep usb
```
those may give you some information

---

### Post by sankarj12 on 2007-04-20
When the computer was booting up, the light lit up on the device, so I guess it is being detected.  Now all I need is to get it to work.  Here's the results of everything:

**sudo lsusb -vv** gave me:
```

Bus 001 Device 004: ID 05dc:0330 Lexar Media, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0x0330 
  bcdDevice            0.01
  iManufacturer           1 LEXAR MEDIA    
  iProduct                2 JD EXPRESSION  
  iSerial                 3 0A4E97010100441
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              120mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 002: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0846 NetGear, Inc.
  idProduct          0x4240 WG111 WiFi (v2)
  bcdDevice           10.40
  iManufacturer           1 GlobespanVirata
  iProduct                2 NETGEAR WG111
  iSerial                 3 3887-0000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         0
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.20-15-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:07.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```  

**sudo lshw** gave me:

```

ubuntu                    
    description: Computer
    product: MS-6119
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.X
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
  *-core
       description: Motherboard
       product: MS-6119 (i440BX)
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.X
       slot: PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 4.51 PG (10/20/98)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium II (Deschutes)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.5.2
          slot: SLOT 1
          size: 400MHz
          capacity: 450MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-cache:0
          description: L1 cache
          physical id: 9
          slot: Internal Cache
          size: 32KB
          capacity: 32KB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: a
          slot: External Cache
          size: 512KB
          capacity: 512KB
          capabilities: synchronous external write-back
     *-memory
          description: System memory
          physical id: 1
          size: 255MB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
          resources: iomemory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage XL AGP 2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 27
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e4000000-e4ffffff ioport:d000-d0ff iomemory:e6000000-e6000fff irq:11
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=64
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f000-f00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: SAMSUNG SV2002H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: RA100-04
                   serial: 0406J1FR805654
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 18GB
                      capabilities: primary bootable
              *-disk:1
                   description: ATA Disk
                   product: ST38641A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 3.15
                   serial: GR547714
                   size: 8063MB
                   capacity: 8063MB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 7671MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      size: 384MB
                      capacity: 384MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hdb5
                         capacity: 384MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: IDE CD-ROM
                   product: LITE-ON CD-ROM LTN-529S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 7S05
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: SAMSUNG CD-R/RW SW-408B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: BS02
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64
             resources: ioport:e000-e01f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: NETGEAR WG111
                   vendor: GlobespanVirata
                   physical id: 1
                   bus info: usb@1:1
                   version: 10.40
                   serial: 3887-0000
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=12.0MB/s
              *-usb:1
                   description: Mass storage device
                   product: JD EXPRESSION
                   vendor: LEXAR MEDIA
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi0
                   version: 0.01
                   serial: 0A4E97010100441
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=120mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: JD EXPRESSION
                      vendor: LEXAR
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 1.00
                      size: 489MB
                      capabilities: removable
                      configuration: ansiversion=1
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                         size: 489MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: FAT12 partition
                            physical id: 1
                            logical name: /dev/sda1
                            capacity: 489MB
                            capabilities: primary
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: e
             bus info: pci@00:0e.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
             resources: ioport:e400-e41f irq:11
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: e.1
             bus info: pci@00:0e.1
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=64
             resources: ioport:e800-e807
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@00:10.0
             logical name: eth0
             version: 10
             serial: 00:48:54:8d:ad:c5
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
             resources: ioport:ec00-ecff iomemory:e8000000-e80000ff irq:5

```

**dmesg | grep usb** gave me:

```

[   37.528470] usbcore: registered new interface driver usbfs
[   37.528577] usbcore: registered new interface driver hub
[   37.528710] usbcore: registered new device driver usb
[   39.565470] usb usb1: configuration #1 chosen from 1 choice
[   39.911756] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   40.081504] usb 1-1: configuration #1 chosen from 1 choice
[   40.323696] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   40.513389] usb 1-2: configuration #1 chosen from 1 choice
[   80.976069] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0F11
[   80.976136] usbcore: registered new interface driver ndiswrapper
[   80.976172] usbcore: registered new interface driver usblp
[   80.976187] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 2417.646076] usb 1-2: USB disconnect, address 3
[ 2417.646545] drivers/usb/class/usblp.c: usblp0: removed
[ 2426.017847] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 2426.186141] usb 1-2: configuration #1 chosen from 1 choice
[ 2426.716265] usbcore: registered new interface driver libusual
[ 2426.950082] usbcore: registered new interface driver usb-storage
[ 2426.952169] usb-storage: device found at 4
[ 2426.952186] usb-storage: waiting for device to settle before scanning
[ 2431.951489] usb-storage: device scan complete


```

---

### Post by Jussi Kukkonen on 2007-04-20
Looks like it's detected as a USB device, but I'm not sure if it looks like it should: lsusb identifies the class,subclass and protocol of the wifi adapter as  "vendor specific" -- not very informative.

---

### Post by sankarj12 on 2007-04-21
> *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: NETGEAR WG111
                   vendor: GlobespanVirata
                   physical id: 1
                   bus info: usb@1:1
                   version: 10.40
                   serial: 3887-0000
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=12.0MB/s

It looks like it is detecting my wireless adapter, but when I enter "iwconfig" it doesn't show up.  I have configured ndiswrapper with the proper drivers.  Should this be  moved to the "Wireless and Networking" section?

---

### Post by ammans on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595). [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all

I have that same problem with that new KUBUNTU FEISTY 7.04, but ONLY when I start up with the usb cables plugged IN.
(This problem wasn't there in 6.10!)

Try this:
Start up the computer with the usb cables NOT plugged in.
Once the computer is up and running for 100% PLUG IN the USB cables.
The external devices will be found automatically and it all will work fine from then on!

What's the problem here, but more importand: What's the solution??

Thanks a lot for your help!

Sunny greetings from the Belgian coast :)

---

