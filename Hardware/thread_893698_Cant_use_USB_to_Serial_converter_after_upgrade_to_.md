---
title: "Cant use USB to Serial converter after upgrade to Hardy"
date: 2008-08-18
forum: Hardware
---

### Post by wroopy on 2008-08-18
Hi!

I've just upgraded my server from Gutsy to Hardy.
Most of my applications is still working (eventhough some fixes where needed). However there is one final thing that doesn't work; my USB <-> Serial converter.  

The converter is identified by the system that the mos7840 module is loaded. But when the module should identify the converter I get the message "probe of 8-1:1.0 failed with error -5".  When running Gutsy everything worked fine.  

See below for log extracts from dmesg from my server running Gutsy and Hardy. I've also included an verbose listing of lsusb on the converter.

**Output from dmesg in Hardy:**
```
[   38.565449] /build/buildd/linux-2.6.24/drivers/usb/serial/mos7840.c: Moschip 7840/7820 USB Serial Driver 1.3.1
[   38.565472] mos7840: probe of 8-1:1.0 failed with error -5
[   38.565480] usbcore: registered new interface driver mos7840

```

**Output from dmesg in Gutsy:**
```
[   34.265121] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/mos7840.c: Moschip 7840/7820 USB Serial Driver 1.3.1
[   34.265140] mos7840 8-1:1.0: Moschip 7840/7820 USB Serial Driver converter detected
[   34.271350] usbcore: registered new interface driver mos7840
```

**lsusb -v**
```
Bus 008 Device 003: ID 9710:7840 MosChip Semiconductor
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0
  bDeviceProtocol       255
  bMaxPacketSize0        64
  idVendor           0x9710 MosChip Semiconductor
  idProduct          0x7840
  bcdDevice            0.01
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
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
      bNumEndpoints           9
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol    255
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               5
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0
  bDeviceProtocol       255
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

I've run out on ideas on how to handle the error. Any ideas?

/Andreas

---

### Post by wroopy on 2008-08-19
To verify I've tested the serial adapter on a Windows computer and it works.
Also tested to run a Kubuntu on the other computer with the same problem.  Hence I assume that there is some kine of error with Hardy.

---

