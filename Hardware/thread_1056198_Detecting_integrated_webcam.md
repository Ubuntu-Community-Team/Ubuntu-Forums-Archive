---
title: "Detecting integrated webcam"
date: 2009-01-31
forum: Hardware
---

### Post by armageddon1 on 2009-01-31
Hi!

I have a laptop with an integrated webcam but I am not sure how to make my computer detect it. I've done some searching and here are the data:

> ~$ luvcview 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

>  lsusb 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 147e:2016  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


> Bus 007 Device 001: ID 0000:0000  
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
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
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
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 006 Device 001: ID 0000:0000  
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
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.7
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
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a12 Cambridge Silicon Radio, Ltd
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
  bcdDevice           19.58
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
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
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 002: ID 147e:2016  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x147e 
  idProduct          0x2016 
  bcdDevice            0.01
  iManufacturer           1 TouchStrip        
  iProduct                2 Fingerprint Sensor   
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.1
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.0
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

I have no /dev/video* directories. And all I can tell about my webcam is that it is a 1.3 Mpixel by ALi Corporation.

uname -a: Linux ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Thank you.

---

### Post by khelben1979 on 2009-01-31
What happens if you use [Skype]("http://www.skype.com") with that webcam? 

Since some hardware in the Linux kernel get's loaded as modules they will only load when they need to.

---

### Post by armageddon1 on 2009-01-31
Hi, khelben1979!

It says "No devices found".

---

### Post by khelben1979 on 2009-01-31
What brand and model is that laptop?

You can run the dmesg command to make it easier for me and others to see what you have over there.

---

### Post by armageddon1 on 2009-01-31
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6c0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6c0000 - 00000000bf6cb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6cb000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7c80
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7C00 checksum 0
[    0.000000] ACPI: RSDP 000F7C00, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BF6C023D, 0094 (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP BF6C7BD2, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BF6C2067, 5AF7 (r2 INTEL  CRESTLNE  6040000 INTL 20050624)
[    0.000000] ACPI: FACS BF6CAFC0, 0040
[    0.000000] ACPI: APIC BF6C7CC6, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET BF6C7D2E, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BF6C7D66, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA BF6C7DA2, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR BF6C7DD4, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: APIC BF6C7DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: SLIC BF6C7E62, 0176 (r1 MSTEST TESTONLY  6040000  LTP        0)
[    0.000000] ACPI: BOOT BF6C7FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT BF6C1A18, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6C1386, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6C085D, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6C07B7, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BF6C02D1, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1040384
[    0.000000] Kernel command line: root=UUID=180dda1c-461f-4389-ad7e-fae359546490 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2394.123 MHz processor.
[   20.626344] Console: colour VGA+ 80x25
[   20.626347] console [tty0] enabled
[   20.626628] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.626869] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.770953] Memory: 3089924k/4194304k available (2177k kernel code, 45104k reserved, 1006k data, 368k init, 2218752k highmem)
[   20.770958] virtual kernel memory layout:
[   20.770959]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.770960]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.770961]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.770961]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.770962]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.770962]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   20.770963]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   20.770965] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.770999] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.771111] hpet clockevent registered
[   20.850979] Calibrating delay using timer specific routine.. 4792.63 BogoMIPS (lpj=9585270)
[   20.850997] Security Framework initialized
[   20.851002] SELinux:  Disabled at boot.
[   20.851012] AppArmor: AppArmor initialized
[   20.851016] Failure registering capabilities with primary security module.
[   20.851021] Mount-cache hash table entries: 512
[   20.851117] Initializing cgroup subsys ns
[   20.851122] Initializing cgroup subsys cpuacct
[   20.851129] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   20.851134] monitor/mwait feature present.
[   20.851135] using mwait in idle threads.
[   20.851139] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.851140] CPU: L2 cache: 4096K
[   20.851142] CPU: Physical Processor ID: 0
[   20.851143] CPU: Processor Core ID: 0
[   20.851144] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   20.851151] Compat vDSO mapped to ffffe000.
[   20.851161] Checking 'hlt' instruction... OK.
[   20.867235] SMP alternatives: switching to UP code
[   20.868389] Early unpacking initramfs... done
[   21.090125] ACPI: Core revision 20070126
[   21.090157] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.100727] CPU0: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0a
[   21.100740] SMP alternatives: switching to SMP code
[   21.101252] Booting processor 1/1 eip 3000
[   21.111598] Initializing CPU#1
[   21.190387] Calibrating delay using timer specific routine.. 4787.86 BogoMIPS (lpj=9575733)
[   21.190392] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[   21.190396] monitor/mwait feature present.
[   21.190398] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.190400] CPU: L2 cache: 4096K
[   21.190401] CPU: Physical Processor ID: 0
[   21.190402] CPU: Processor Core ID: 1
[   21.190403] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   21.190985] CPU1: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0a
[   21.191004] Total of 2 processors activated (9580.50 BogoMIPS).
[   21.191171] ENABLING IO-APIC IRQs
[   21.191348] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.338219] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   21.358197] Brought up 2 CPUs
[   21.358216] CPU0 attaching sched-domain:
[   21.358217]  domain 0: span 03
[   21.358219]   groups: 01 02
[   21.358221] CPU1 attaching sched-domain:
[   21.358222]  domain 0: span 03
[   21.358223]   groups: 02 01
[   21.358382] net_namespace: 64 bytes
[   21.358387] Booting paravirtualized kernel on bare hardware
[   21.358728] Time: 16:24:53  Date: 01/31/09
[   21.358749] NET: Registered protocol family 16
[   21.358881] EISA bus registered
[   21.358884] ACPI: bus type pci registered
[   21.359246] PCI: PCI BIOS revision 3.00 entry at 0xfdda1, last bus=12
[   21.359247] PCI: Using configuration type 1
[   21.359255] Setting up standard PCI resources
[   21.361139] ACPI: EC: Look up EC in DSDT
[   21.362452] ACPI: BIOS _OSI(Linux) query ignored
[   21.362453] ACPI: DMI System Vendor: CLEVO CO.
[   21.362454] ACPI: DMI Product Name: M540R
[   21.362455] ACPI: DMI Product Version: Not Applicable
[   21.362456] ACPI: DMI Board Name: M540R
[   21.362457] ACPI: DMI BIOS Vendor: Phoenix
[   21.362458] ACPI: DMI BIOS Date: 08/24/2007
[   21.362459] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[   21.362461] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[   21.363097] ACPI: Interpreter enabled
[   21.363098] ACPI: (supports S0 S3 S4 S5)
[   21.363108] ACPI: Using IOAPIC for interrupt routing
[   21.368132] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[   21.368133] ACPI: EC: driver started in poll mode
[   21.368164] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.369194] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   21.369198] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   21.370237] PCI: Transparent bridge - 0000:00:1e.0
[   21.370294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.370562] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   21.370653] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   21.370743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   21.370833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   21.370923] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   21.371012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   21.371112] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   21.380040] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   21.380115] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.380188] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   21.380259] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.380330] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   21.380401] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   21.380471] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   21.380543] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.380655] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.380677] pnp: PnP ACPI init
[   21.380682] ACPI: bus type pnp registered
[   21.381285] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   21.382379] pnp: PnP ACPI: found 11 devices
[   21.382380] ACPI: ACPI bus type pnp unregistered
[   21.382382] PnPBIOS: Disabled by ACPI PNP
[   21.382531] PCI: Using ACPI for IRQ routing
[   21.382533] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.485999] NET: Registered protocol family 8
[   21.486000] NET: Registered protocol family 20
[   21.486025] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.486028] hpet0: 3 64-bit timers, 14318180 Hz
[   21.487052] AppArmor: AppArmor Filesystem Enabled
[   21.489873] Time: tsc clocksource has been installed.
[   21.489882] Switched to high resolution mode on CPU 0
[   21.489964] Switched to high resolution mode on CPU 1
[   21.513827] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   21.513829] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   21.513831] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   21.513833] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   21.513835] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.513837] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   21.513839] system 00:01: iomem range 0x0-0x0 could not be reserved
[   21.513841] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   21.513847] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   21.513851] system 00:06: ioport range 0x680-0x69f has been reserved
[   21.513853] system 00:06: ioport range 0x800-0x80f has been reserved
[   21.513855] system 00:06: ioport range 0x1000-0x107f has been reserved
[   21.513857] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   21.513859] system 00:06: ioport range 0x1640-0x164f has been reserved
[   21.513861] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   21.544125] PCI: Bridge: 0000:00:1c.0
[   21.544126]   IO window: disabled.
[   21.544132]   MEM window: f0e00000-f0efffff
[   21.544135]   PREFETCH window: disabled.
[   21.544140] PCI: Bridge: 0000:00:1c.1
[   21.544142]   IO window: 2000-2fff
[   21.544147]   MEM window: f0600000-f07fffff
[   21.544151]   PREFETCH window: f0000000-f01fffff
[   21.544156] PCI: Bridge: 0000:00:1c.2
[   21.544159]   IO window: 3000-3fff
[   21.544164]   MEM window: f0800000-f09fffff
[   21.544168]   PREFETCH window: f0200000-f03fffff
[   21.544173] PCI: Bridge: 0000:00:1c.3
[   21.544175]   IO window: 4000-4fff
[   21.544180]   MEM window: f0a00000-f0bfffff
[   21.544184]   PREFETCH window: f0400000-f05fffff
[   21.544190] PCI: Bridge: 0000:00:1c.4
[   21.544191]   IO window: disabled.
[   21.544196]   MEM window: disabled.
[   21.544199]   PREFETCH window: disabled.
[   21.544205] PCI: Bridge: 0000:00:1c.5
[   21.544206]   IO window: disabled.
[   21.544211]   MEM window: disabled.
[   21.544215]   PREFETCH window: disabled.
[   21.544220] PCI: Bridge: 0000:00:1e.0
[   21.544222]   IO window: 5000-5fff
[   21.544228]   MEM window: f0f00000-f0ffffff
[   21.544231]   PREFETCH window: disabled.
[   21.544258] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   21.544263] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.544285] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   21.544290] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.544312] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.544317] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.544339] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   21.544343] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   21.544364] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 16
[   21.544369] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   21.544391] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 17
[   21.544395] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   21.544409] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.544416] NET: Registered protocol family 2
[   21.581731] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.581894] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.582198] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.582355] TCP: Hash tables configured (established 131072 bind 65536)
[   21.582357] TCP reno registered
[   21.593755] checking if image is initramfs... it is
[   22.064932] Freeing initrd memory: 7312k freed
[   22.065056] Simple Boot Flag at 0x36 set to 0x1
[   22.065499] audit: initializing netlink socket (disabled)
[   22.065509] audit(1233419094.085:1): initialized
[   22.065707] highmem bounce pool size: 64 pages
[   22.067075] VFS: Disk quotas dquot_6.5.1
[   22.067126] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.067219] io scheduler noop registered
[   22.067220] io scheduler anticipatory registered
[   22.067222] io scheduler deadline registered
[   22.067229] io scheduler cfq registered (default)
[   22.067239] Boot video device is 0000:00:02.0
[   22.067436] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.067491] assign_interrupt_mode Found MSI capability
[   22.067539] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.067630] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.067685] assign_interrupt_mode Found MSI capability
[   22.067730] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.067819] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   22.067874] assign_interrupt_mode Found MSI capability
[   22.067918] Allocate Port Service[0000:00:1c.2:pcie00]
[   22.068005] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   22.068060] assign_interrupt_mode Found MSI capability
[   22.068104] Allocate Port Service[0000:00:1c.3:pcie00]
[   22.068192] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   22.068247] assign_interrupt_mode Found MSI capability
[   22.068291] Allocate Port Service[0000:00:1c.4:pcie00]
[   22.068378] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   22.068433] assign_interrupt_mode Found MSI capability
[   22.068477] Allocate Port Service[0000:00:1c.5:pcie00]
[   22.068673] isapnp: Scanning for PnP cards...
[   22.422342] isapnp: No Plug & Play device found
[   22.439417] Real Time Clock Driver v1.12ac
[   22.439589] hpet_resources: 0xfed00000 is busy
[   22.439612] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.440446] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.440494] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.440561] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.444729] i8042.c: Detected active multiplexing controller, rev 1.1.
[   22.447254] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.447258] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   22.447259] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   22.447261] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   22.447263] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   22.469227] mice: PS/2 mouse device common for all mice
[   22.469302] EISA: Probing bus 0 at eisa.0
[   22.469308] Cannot allocate resource for EISA slot 1
[   22.469310] Cannot allocate resource for EISA slot 2
[   22.469312] Cannot allocate resource for EISA slot 3
[   22.469313] Cannot allocate resource for EISA slot 4
[   22.469314] Cannot allocate resource for EISA slot 5
[   22.469327] EISA: Detected 0 cards.
[   22.469329] cpuidle: using governor ladder
[   22.469331] cpuidle: using governor menu
[   22.469388] NET: Registered protocol family 1
[   22.469407] Using IPI No-Shortcut mode
[   22.469428] registered taskstats version 1
[   22.469516]   Magic number: 9:370:440
[   22.469551]   hash matches device 0000:00:1c.1
[   22.469559] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.469560] EDD information not available.
[   22.469732] Freeing unused kernel memory: 368k freed
[   22.505459] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.617623] fuse init (API version 7.9)
[   23.631866] ACPI: SSDT BF6C0FEB, 02EA (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   23.632025] ACPI: SSDT BF6C0ABC, 04AA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   23.633455] Monitor-Mwait will be used to enter C-1 state
[   23.633457] Monitor-Mwait will be used to enter C-2 state
[   23.633459] Monitor-Mwait will be used to enter C-3 state
[   23.633546] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   23.633550] ACPI: Processor [CPU0] (supports 8 throttling states)
[   23.633716] ACPI: SSDT BF6C12D5, 00B1 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   23.633861] ACPI: SSDT BF6C0F66, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   23.634571] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   23.634574] ACPI: Processor [CPU1] (supports 8 throttling states)
[   23.637015] ACPI: Thermal Zone [THRM] (57 C)
[   23.870828] usbcore: registered new interface driver usbfs
[   23.870845] usbcore: registered new interface driver hub
[   23.871159] usbcore: registered new device driver usb
[   23.878454] USB Universal Host Controller Interface driver v3.0
[   23.878496] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   23.878507] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.878511] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.878711] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   23.878742] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   23.878832] usb usb1: configuration #1 chosen from 1 choice
[   23.878848] hub 1-0:1.0: USB hub found
[   23.878852] hub 1-0:1.0: 2 ports detected
[   23.953633] SCSI subsystem initialized
[   23.985636] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   23.985646] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.985650] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.985667] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   23.985697] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001840
[   23.985784] usb usb2: configuration #1 chosen from 1 choice
[   23.985800] hub 2-0:1.0: USB hub found
[   23.985804] hub 2-0:1.0: 2 ports detected
[   23.989299] libata version 3.00 loaded.
[   24.089489] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[   24.089498] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.089502] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.089518] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   24.089547] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001860
[   24.089629] usb usb3: configuration #1 chosen from 1 choice
[   24.089646] hub 3-0:1.0: USB hub found
[   24.089650] hub 3-0:1.0: 2 ports detected
[   24.193303] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   24.193312] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.193316] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.193335] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   24.193364] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[   24.193446] usb usb4: configuration #1 chosen from 1 choice
[   24.193463] hub 4-0:1.0: USB hub found
[   24.193466] hub 4-0:1.0: 2 ports detected
[   24.293140] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.293148] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.293152] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.293167] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   24.293197] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[   24.293275] usb usb5: configuration #1 chosen from 1 choice
[   24.293291] hub 5-0:1.0: USB hub found
[   24.293294] hub 5-0:1.0: 2 ports detected
[   24.397015] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   24.397030] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   24.397035] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   24.397066] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   24.400969] ehci_hcd 0000:00:1a.7: debug port 1
[   24.400975] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   24.400979] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf1204000
[   24.416815] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.416894] usb usb6: configuration #1 chosen from 1 choice
[   24.416911] hub 6-0:1.0: USB hub found
[   24.416916] hub 6-0:1.0: 4 ports detected
[   24.472716] Clocksource tsc unstable (delta = -6795472680 ns)
[   24.476785] Time: hpet clocksource has been installed.
[   24.477837] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[   24.477848] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.477851] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.477868] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   24.481763] ehci_hcd 0000:00:1d.7: debug port 1
[   24.481768] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.481772] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xf1204400
[   24.486260] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.486350] usb usb7: configuration #1 chosen from 1 choice
[   24.486369] hub 7-0:1.0: USB hub found
[   24.486373] hub 7-0:1.0: 6 ports detected
[   24.492646] r8169 Gigabit Ethernet driver 2.2LK loaded
[   24.492669] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   24.492686] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   24.492960] eth0: RTL8168b/8111b at 0xf8846000, 00:90:f5:61:da:52, XID 38000000 IRQ 217
[   24.494108] ACPI: PCI Interrupt 0000:0c:09.0[A] -> GSI 19 (level, low) -> IRQ 19
[   24.546936] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f0f00000-f0f007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.552024] ata_piix 0000:00:1f.2: version 2.12
[   24.552030] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   24.561186] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   24.561213] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.561332] scsi0 : ata_piix
[   24.561460] scsi1 : ata_piix
[   24.562086] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18e0 irq 14
[   24.562088] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18e8 irq 15
[   24.571235] ata1.00: ATA-7: ST9200420ASG, 3.AAA, max UDMA/133
[   24.571238] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.573131] ata1.00: configured for UDMA/133
[   24.577754] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   24.585207] usb 2-2: configuration #1 chosen from 1 choice
[   24.596340] ata2.00: ATAPI: Optiarc DVD RW AD-7543A, 1-00, max UDMA/33
[   24.603072] ata2.00: configured for UDMA/33
[   24.603231] scsi 0:0:0:0: Direct-Access     ATA      ST9200420ASG     3.AA PQ: 0 ANSI: 5
[   24.604114] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7543A  1-00 PQ: 0 ANSI: 5
[   24.614161] Driver 'sd' needs updating - please use bus_type methods
[   24.614207] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   24.614215] sd 0:0:0:0: [sda] Write Protect is off
[   24.614217] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.614229] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.614263] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   24.614270] sd 0:0:0:0: [sda] Write Protect is off
[   24.614272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.614283] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.614285]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.625831]  sda1 sda2 < sda5 > sda3
[   24.661681]  sda3: <bsd: sda6 sda7 sda8 >
[   24.661807] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.665418] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.665432] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.667190] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.667193] Uniform CD-ROM driver Revision: 3.20
[   24.667222] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.910797] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   24.946061] Attempting manual resume
[   24.946063] swsusp: Resume From Partition 8:5
[   24.946064] PM: Checking swsusp image.
[   24.946239] PM: Resume from disk failed.
[   24.967981] kjournald starting.  Commit interval 5 seconds
[   24.968008] EXT3-fs: mounted filesystem with ordered data mode.
[   25.050863] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000090f50061da52]
[   25.098885] usb 5-1: configuration #1 chosen from 1 choice
[   33.360737] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.397784] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.601816] input: Power Button (FF) as /devices/virtual/input/input2
[   33.662589] ACPI: Power Button (FF) [PWRF]
[   33.662635] input: Power Button (CM) as /devices/virtual/input/input3
[   33.677567] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   33.695226] iTCO_vendor_support: vendor-support=0
[   33.726523] ACPI: Power Button (CM) [PWB]
[   33.726566] input: Sleep Button (CM) as /devices/virtual/input/input5
[   33.747454] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.817568] ACPI: Sleep Button (CM) [SLPB]
[   33.817610] input: Lid Switch as /devices/virtual/input/input6
[   33.819318] Linux agpgart interface v0.102
[   33.837105] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b1, caps: 0xa04713/0x204000
[   33.853463] ACPI: Lid Switch [LID]
[   33.853860] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   33.874853] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   33.879350] agpgart: Detected an Intel 965GM Chipset.
[   33.880837] agpgart: Detected 7676K stolen memory.
[   33.893230] agpgart: AGP aperture is 256M @ 0xd0000000
[   33.911171] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   33.972437] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   33.972480] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.071226] ACPI: AC Adapter [AC] (on-line)
[   34.082991] ACPI: Battery Slot [BAT0] (battery present)
[   34.083053] ACPI: WMI-Acer: Mapper loaded
[   34.346878] Bluetooth: Core ver 2.11
[   34.356310] NET: Registered protocol family 31
[   34.356312] Bluetooth: HCI device and connection manager initialized
[   34.356314] Bluetooth: HCI socket layer initialized
[   34.361100] hci_usb: Unknown symbol hci_suspend_dev
[   34.361123] hci_usb: Unknown symbol hci_free_dev
[   34.361387] hci_usb: Unknown symbol hci_resume_dev
[   34.361442] hci_usb: Unknown symbol hci_alloc_dev
[   34.361544] hci_usb: Unknown symbol hci_unregister_dev
[   34.361606] hci_usb: Unknown symbol hci_recv_fragment
[   34.361658] hci_usb: Unknown symbol hci_register_dev
[   34.375874] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   34.375876] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   34.375949] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   34.375958] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.375971] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   34.379686] Bluetooth: HCI USB driver ver 2.9
[   34.381367] usbcore: registered new interface driver hci_usb
[   34.669162] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   34.669181] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.744493] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   34.744763] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   34.934522] loop: module loaded
[   34.996465] lp: driver loaded but no devices found
[   35.140204] Adding 7960168k swap on /dev/sda5.  Priority:-1 extents:1 across:7960168k
[   35.995945] EXT3 FS on sda1, internal journal
[   37.454455] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.801586] No dock devices found.
[   39.078455] ppdev: user-space parallel port driver
[   39.167392] audit(1233419119.350:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5167 profile="/usr/sbin/cupsd" namespace="default"
[   40.870467] apm: BIOS not found.
[   44.694219] NET: Registered protocol family 17
[   47.669934] r8169: eth0: link up
[   47.669949] r8169: eth0: link up
[   47.876688] Bluetooth: L2CAP ver 2.9
[   47.876695] Bluetooth: L2CAP socket layer initialized
[   48.028293] Bluetooth: RFCOMM socket layer initialized
[   48.028311] Bluetooth: RFCOMM TTY layer initialized
[   48.028316] Bluetooth: RFCOMM ver 1.8
[   50.857268] [drm] Initialized drm 1.1.0 20060810
[   50.898690] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   50.898705] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   50.898801] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   50.948215] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   52.594786] NET: Registered protocol family 10
[   52.595275] lo: Disabled Privacy Extensions
[   52.597139] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.397276] CPU0 attaching NULL sched-domain.
[   73.397286] CPU1 attaching NULL sched-domain.
[   73.420308] CPU0 attaching sched-domain:
[   73.420317]  domain 0: span 03
[   73.420322]   groups: 01 02
[   73.420329] CPU1 attaching sched-domain:
[   73.420332]  domain 0: span 03
[   73.420336]   groups: 02 01
[  100.624248] wlan0: Initial auth_alg=0
[  100.624253] wlan0: authenticate with AP 00:1a:1e:a9:59:80
[  100.628064] wlan0: Initial auth_alg=0
[  100.628068] wlan0: authenticate with AP 00:1a:1e:a9:59:80
[  100.628075] wlan0: RX authentication from 00:1a:1e:a9:59:80 (alg=0 transaction=2 status=0)
[  100.628077] wlan0: authenticated
[  100.628079] wlan0: associate with AP 00:1a:1e:a9:59:80
[  100.628085] wlan0: authentication frame received from 00:1a:1e:a9:59:80, but not in authenticate state - ignored
[  100.629722] wlan0: authentication frame received from 00:1a:1e:a9:59:80, but not in authenticate state - ignored
[  100.635658] wlan0: RX AssocResp from 00:1a:1e:a9:59:80 (capab=0x421 status=0 aid=3)
[  100.635662] wlan0: associated
[  100.637204] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  111.079501] wlan0: no IPv6 routers present
[  115.724848] wlan0: no IPv6 routers present
[ 6329.186962] process `skype' is using obsolete setsockopt SO_BSDCOMPAT


The computer is a Clevo M548R.

---

### Post by khelben1979 on 2009-02-01
I think you must compile your own Linux kernel in order to get support for that webcam. Although I'm not sure if the Linux kernel supports it, there's a chance it will. I did some Google searches but I couldn't find anything useful on the subject. 

Getting a usb webcam and connect to it would be the easiest thing to get a webcam up and running at the present without going for another Linux kernel.

Maybe someone can find something better on this?

---

### Post by armageddon1 on 2009-02-02
Hi khelben1979! The webcam is now detected!
> lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 147e:2016  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

lsusb -v:

> Bus 006 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0402 ALi Corp.
  idProduct          0x5602 Video Camera Controller
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB2.0 Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          101
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1300  3x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
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
I've tried easycam but while it says (I think) the installation was completed it is not able to capture anything. Skype finds something called "BisonCam (dev/video0)".
Cheers.

---

