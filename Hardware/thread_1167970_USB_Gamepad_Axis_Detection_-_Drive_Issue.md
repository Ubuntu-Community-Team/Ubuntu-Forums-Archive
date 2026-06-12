---
title: "USB Gamepad Axis Detection - Drive Issue?"
date: 2009-05-23
forum: Hardware
---

### Post by Sud on 2009-05-23
Hi All,

Need help to get a USB Gamepad working in Ubuntu (Hardy 8.04), that is working fine in Windows XP.  This is a Zebronics ZEB-50JP USB Gamepad (listed in [http://www.zebronics.net/gamingaccessories.asp](http://www.zebronics.net/gamingaccessories.asp)).  This is detected as having 2 axes (D-pad) and 10 buttons in Windows, but is detected as having "6" axes and 10 buttons in Ubuntu, for e.g. with jscalibrator.  Also, the X,Y axes appear to have got incorrectly mapped to RX and RY.  Not sure if this could be a driver issue.

I am attaching the dmesg and lsusb output below for reference.  Please help to resolve this issue and do let me know if any further information is required.

Thanks.

dmesg output is as follows

[18444.192889] usb 2-1: new low speed USB device using uhci_hcd and address 4
[18444.360530] usb 2-1: configuration #1 chosen from 1 choice
[10531.435588] input: USB Gamepad  as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input11
[10531.462987] input,hidraw1: USB HID v1.10 Joystick [USB Gamepad ] on usb-0000:00:1d.1-1


The lsusb -v output is as follows

Bus 002 Device 004: ID 0079:0011  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0079 
  idProduct          0x0011 
  bcdDevice            1.06
  iManufacturer           0 
  iProduct                2 USB Gamepad 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     101
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
Device Status:     0x0000
  (Bus Powered)

---

