---
title: "Microsoft Bluetooth Dongle Not Detected"
date: 2020-02-08
forum: Hardware
---

### Post by eyeofreason on 2020-02-08
I'm trying to get a Microsoft Bluetooth dongle working in Ubuntu 18.04. Blueman says that there are no Bluetooth devices detected. 

$ lsusb
Bus 002 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
[COLOR=#ff0000]Bus 002 Device 014: ID 045e:02e6 Microsoft Corp. [/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


 I apologise if this is posted elsewhere, and I appreciate any help.

---

### Post by gdesilva on 2020-06-03
Exactly the same issue here with US 20.04. I had it working in older versions but works OK in Lubuntu 18.04.

I have blueman-manager icon greyed out. If I run blueman-manager I get following output

[I]blueman-manager version 2.1.2 starting
blueman-manager 16.01.40 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 16.01.40 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting[/I]


lsusb -v returns the following


[I]Bus 002 Device 012: ID 045e:071d Microsoft Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x071d 
  bcdDevice            2.50
  iManufacturer           1 Microsoft
  iProduct                2 Microsoft® 2.4GHz Transceiver V1.0
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x003b
    bNumInterfaces          2
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
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     571
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
Device Status:     0x0000
  (Bus Powered)


[/I]Plugged in a Burrows mini bluetooth dongle and works without any issues but 'bt-adapter -l' does not list any adapters.

---

