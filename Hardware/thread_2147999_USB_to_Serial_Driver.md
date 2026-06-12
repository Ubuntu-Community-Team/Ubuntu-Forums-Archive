---
title: "USB to Serial Driver?"
date: 2013-05-23
forum: Hardware
---

### Post by kmand on 2013-05-23
I have a device with a USB port that shows up as a Cypress Semiconductor USB to Serial under lsusb. Apparently the software expects linux to see a tty port that it will use to access the device. However, I don't see one. I assume there is a missing driver.

Any suggestions?  This is on Ubuntu 13.04. Here is specifically what lsusb -v sees

Bus 002 Device 011: ID 0665:5161 Cypress Semiconductor USB to Serial
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0665 Cypress Semiconductor
  idProduct          0x5161 USB to Serial
  bcdDevice            0.02
  iManufacturer           1 Cypress Semiconductor
  iProduct                2 USB to Serial
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          3 
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
      iInterface              4 Sample HID
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      27
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
        bInterval              32
Device Status:     0x0000
  (Bus Powered)

---

