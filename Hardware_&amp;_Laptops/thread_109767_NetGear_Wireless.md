---
title: "NetGear Wireless"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by musicalmike on 2005-12-29
I resently took an old compaq running Windows XP, and installed Ubuntu on it. While it still had XP on it, I would use a NetGear USB 2.0 Wirless adapter to get internet access. Unfortunately, I am having trouble getting it to work on ubuntu. I currentlly have the notebook wired up to our cable modem for internet access however, this solution is NOT portable which sort of defeats the point of having the lap top. Is there any way of getting the NetGear wireless adapter to work with ubuntu? If not, are there any wireless devices that work with ubuntu?

---

### Post by Lambert on 2005-12-29
Little more info is needed such as what the model # of the usb device is? You may need to install a driver to get it to work.

You can also post output of these commands

sudo lsusb -v

sudo lshw

you can limit the post to just the usb device if you can tell which one it is.


There are many wireless devices that work on ubuntu, usb seems to be a little behind pcmcia in supported devices but with some configuring you can get them to work. 

If you want to get a new device go here as this is a list of devices and reports from users on whether they work.

[https://wiki.ubuntu.com/WirelessNetworkCards](https://wiki.ubuntu.com/WirelessNetworkCards)

---

### Post by musicalmike on 2005-12-29
Unfortunately, I don't know much more about the divice. All I know about the divice is the model number is WG111 and that it is a USB 2.0 device. I doubt weather this will be enough information. Its connection speed is 54 Mbps.

heres the output of the commands

root@ubuntu:~# sudo lsusb -v

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-9-386 ohci_hcd
  iProduct                2 ALi Corporation USB 1.1 Controller (#2)
  iSerial                 1 0000:00:0f.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
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
  nNbrPorts             4
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0x80
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power

Bus 001 Device 005: ID 0846:4240 NetGear, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0846 NetGear, Inc.
  idProduct          0x4240
  bcdDevice           10.20
  iManufacturer           1 GlobespanVirata
  iProduct                2 Cohiba 3887 rev0
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

Bus 001 Device 004: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x007d Notebook Optical Mouse
  bcdDevice            0.00
  iManufacturer           1 Microsoft
  iProduct                3 Microsoft 3-Button Mouse with IntelliEye?
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 HID Mouse
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              5 EndPoint1 Int Pipe
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-9-386 ohci_hcd
  iProduct                2 ALi Corporation USB 1.1 Controller
  iSerial                 1 0000:00:02.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
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
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x78
  PortPwrCtrlMask    0x01
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0103 power enable connect
root@ubuntu:~# sudo lshw
ubuntu
    description: Notebook
    product: Presario 900
    vendor: Compaq
    version: 0100
    serial: 1V27KSB124RS
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook uuid=00511C67-AE63-0010-B255-480C0275425A
  *-core
       description: Motherboard
       product: 07D4h
       vendor: Compaq
       physical id: 0
       version: KBC Revision: 1320
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 0F02 (05/24/02)
          size: 108KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) XP 1700+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.0
          slot: U23
          size: 1466MHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 256KB
             capacity: 1MB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 256KB
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: U5
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: U6
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: AGP Bridge [IGP 320M]
          vendor: ATI Technologies Inc
          physical id: f8000000
          bus info: pci@00:00.0
          version: 13
          width: 32 bits
          clock: 66MHz
          resources: iomemory:f8000000-fbffffff iomemory:f4400000-f4400fff
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 320M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility U1
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 32MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f6000000-f7ffffff ioport:9000-90ff iomemory:f4100000-f410ffff irq:10
        *-usb:0
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
             resources: iomemory:f4014000-f4014fff irq:11
           *-usbhost
                product: ALi Corporation USB 1.1 Controller
                vendor: Linux 2.6.12-9-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye?
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Cohiba 3887 rev0
                   vendor: GlobespanVirata
                   physical id: 2
                   bus info: usb@1:2
                   version: 10.20
                   serial: 3887-0000
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:f4016000-f4016fff irq:11
           *-usbhost
                product: ALi Corporation USB 1.1 Controller (#2)
                vendor: Linux 2.6.12-9-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
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
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451
             resources: ioport:8400-84ff iomemory:f4015000-f4015fff irq:5
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:f000000-f000fff irq:10
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth0
             version: 20
             serial: 00:08:02:9e:15:ca
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139cp driverversion=1.2 duplex=full ip=192.168.0.3 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:8800-88ff iomemory:f4017800-f40178ff irq:11
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: c
             bus info: pci@00:0c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:f4000000-f400ffff ioport:8098-809f irq:10
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE
             resources: ioport:8080-808f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HTS541040G9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MB2OA60A
                   serial: MPB2LAX2H3PYJM
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma5 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: SD-R2102
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1A16
                   serial: 624H218819
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 13
             bus info: pci@00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394
             resources: iomemory:f4017000-f40177ff iomemory:f4010000-f4013fff irq:10

---

### Post by daahli on 2005-12-30
hey,

I've also been trying to get this thing working. Apparently there's a native linux driver available from Realtek. See [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187)

However, I'm a newbie and have no idea how to install the driver :( 

I'd really appreciate some help.

Thanks!

---

