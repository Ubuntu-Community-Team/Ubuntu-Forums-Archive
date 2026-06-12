---
title: "USB gamepads no longer detected"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by Orestes on 2006-09-23
Hi folks,

I've been using a couple of ps2 controllers with adapters to use zSNES for about a week know, and I was having great fun on Mario Kart ;).

After a software upgrade, I plugged my controller in, and lo! It no longer works. It used to register with the USB system - I would get output form lsusb, no problems in dmesg and hotplug would create me a /dev/input/js0 node.

Now I plug them in, I get no device node, dmesg gives me:
```

[17182849.440000] usb 2-3: new low speed USB device using ohci_hcd and address 2[17182849.652000] usb 2-3: unable to read config index 0 descriptor/start
[17182849.652000] usb 2-3: can't read configurations, error -75
[17182849.832000] usb 2-3: new low speed USB device using ohci_hcd and address 3[17182850.028000] usb 2-3: device descriptor read/all, error -110
[17182850.208000] usb 2-3: new low speed USB device using ohci_hcd and address 4[17182850.240000] usb 2-3: unable to read config index 0 descriptor/all
[17182850.240000] usb 2-3: can't read configurations, error -84
[17182850.420000] usb 2-3: new low speed USB device using ohci_hcd and address 5[17182850.444000] usb 2-3: device descriptor read/all, error 2
[17182916.724000] usb 2-3: new low speed USB device using ohci_hcd and address 6[17182916.908000] usb 2-3: device descriptor read/64, error -84
[17182917.420000] usb 2-3: device descriptor read/all, error -110
[17182917.600000] usb 2-3: new low speed USB device using ohci_hcd and address 7[17182917.780000] usb 2-3: device descriptor read/64, error 4
[17182918.080000] usb 2-3: device descriptor read/all, error -110
[17182918.260000] usb 2-3: new low speed USB device using ohci_hcd and address 8[17182918.484000] usb 2-3: device descriptor read/8, error -110
[17182918.604000] usb 2-3: device descriptor read/8, error -110
[17182918.884000] usb 2-3: new low speed USB device using ohci_hcd and address 9[17182918.904000] usb 2-3: device descriptor read/8, error -110
[17182919.024000] usb 2-3: device descriptor read/8, error -110
[17183051.292000] usb 2-3: new low speed USB device using ohci_hcd and address 10
[17183051.488000] usb 2-3: device descriptor read/all, error -110
[17183051.668000] usb 2-3: new low speed USB device using ohci_hcd and address 11
[17183051.864000] usb 2-3: device descriptor read/all, error -110
[17183052.044000] usb 2-3: new low speed USB device using ohci_hcd and address 12
[17183052.064000] usb 2-3: device descriptor read/8, error -110
[17183052.184000] usb 2-3: device descriptor read/8, error -110
[17183052.464000] usb 2-3: new low speed USB device using ohci_hcd and address 13
[17183052.484000] usb 2-3: device descriptor read/8, error -110
[17183052.604000] usb 2-3: device descriptor read/8, error -110

```

Now I know they used to register as high-speed devices. My Asuro IR serial device hotplugs just fine, as does my external USB HD. I'll post my lsusb output too in case it helps:

```

Bus 003 Device 002: ID 0424:a700 Standard Microsystems Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x0424 Standard Microsystems Corp.
  idProduct          0xa700
  bcdDevice            0.00
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      1 Single TT
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 TT per port
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0089
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood      128 * 2 milli seconds
  bHubContrCurrent     49 milli Ampere
  DeviceRemovable    0x58
  PortPwrCtrlMask    0xc0
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 003 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE AdapterDevice Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0x6830 USB-2.0 IDE Adapter
  bcdDevice            0.01
  iManufacturer          56 Cypress Semiconductor
  iProduct               78 USB2.0 Storage Device
  iSerial               100 DEF107679C83
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
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
Device Status:     0x0001
  Self Powered

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-27-386 ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:03.2
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
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0xc0
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0503 highspeed power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0000
   Port 6: 0000.0000
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-27-386 ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:03.1
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
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0x01
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0301 lowspeed power connect
Device Status:     0x0001
  Self Powered

Bus 001 Device 007: ID 0403:6001 Future Technology Devices International, Ltd 8-bit FIFO
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x6001 8-bit FIFO
  bcdDevice            4.00
  iManufacturer           1 AREXX
  iProduct                2 ASURO USB-IR-Transceiver
  iSerial                 3 AXO77TGQ
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
    MaxPower               40mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 ASURO USB-IR-Transceiver
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
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-27-386 ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:03.0
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
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0x02
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0103 power enable connect
Device Status:     0x0001
  Self Powered

```

I've tried manually modprobing usbhid and joydev, and still I get the errors in dmesg.
:confused: 

Any help would really be greatly appreciated.

---

### Post by Orestes on 2006-10-02
Update:

THe USB gamepad works fine through my BenQ monitor's integral hub.
```
[17199974.692000] usb 3-6: reset high speed USB device using ehci_hcd and address 6
[17199974.940000] usb 3-6: reset high speed USB device using ehci_hcd and address 6
[17199975.188000] usb 3-6: reset high speed USB device using ehci_hcd and address 6
[17199975.436000] usb 3-6: reset high speed USB device using ehci_hcd and address 6
[17199986.136000] usb 3-6: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -71
[17202158.360000] usb 3-2.2: USB disconnect, address 5
[17202161.632000] usb 3-2.2: new low speed USB device using ehci_hcd and address 8
[17202161.728000] input: USB Gamepad  as /class/input/input4
[17202161.728000] input: USB HID v1.10 Joystick [USB Gamepad ] on usb-0000:00:03.2-2.2
```

However, through my PC's integrated USB ports(Works with smc and USB serial devices btw):

```
[17202247.504000] usb 2-3: new low speed USB device using ohci_hcd and address 3
[17202247.700000] usb 2-3: device descriptor read/all, error -110
[17202247.880000] usb 2-3: new low speed USB device using ohci_hcd and address 4
[17202248.080000] usb 2-3: device descriptor read/all, error -110
[17202248.260000] usb 2-3: new low speed USB device using ohci_hcd and address 5
[17202248.280000] usb 2-3: device descriptor read/8, error -110
[17202248.400000] usb 2-3: device descriptor read/8, error -110
[17202248.680000] usb 2-3: new low speed USB device using ohci_hcd and address 6
[17202248.700000] usb 2-3: device descriptor read/8, error -110
[17202248.820000] usb 2-3: device descriptor read/8, error -110
```

The device desciptor isn't being read properly, so the USB subsystem is using ohci_hcd instead of ehci_hcd. It's also registering 4 usb devices.

](*,) 

Anyone got any thoughts?

---

### Post by Orestes on 2006-10-06
Overwhelmed though I am with responses :P, I'm currently thinking that one socket on my mainboard is USB1.0, while the rear sockets are USB2.0. WHich seems kind of odd - If you are going to provide a backwards compatible USB2.0 interface, why use another chip (ie, extra cost) to incorporate extra ports? The original system can support up to 127 high speed interfaces. Couldn't AsRock just interface with that rather than adding a USB1.0 chip?

---

