---
title: "Panasonic High Speed Color Scanner KV-S3065C"
date: 2010-10-25
forum: Hardware
---

### Post by n8bounds on 2010-10-25
I have the following USB scanner:

```
Bus 002 Device 005: ID 04da:1003 Panasonic (Matsushita) 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04da Panasonic (Matsushita)
  idProduct          0x1003 
  bcdDevice            1.00
  iManufacturer           1 Panasonic 
  iProduct                2 Panasonic High Speed Color Scanner KV-S3065C 
  iSerial                 3 A20070116154157
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
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
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
```


Which does not appear as an available scanner via Simple Scan or Xsane. My ScanJet 3300C works fine, however. This scanner works properly (from Windows) on the same PC.

This is the hardware in question: [http://catalog2.panasonic.com/webapp/wcs/stores/servlet/ModelDetail?storeId=11201&catalogId=13051&itemId=87070&catGroupId=13857&surfModel=KV-S3065CL&displayTab=R](http://catalog2.panasonic.com/webapp/wcs/stores/servlet/ModelDetail?storeId=11201&catalogId=13051&itemId=87070&catGroupId=13857&surfModel=KV-S3065CL&displayTab=R)

I don't even know where to start....

---

### Post by drpaul on 2010-10-25
What software are you using on Windows? Have you tried communicating with the SANE folks to see if it supports that hardware? You could even try to use SANE under Windows to see if it works.

HTH

Paul

---

