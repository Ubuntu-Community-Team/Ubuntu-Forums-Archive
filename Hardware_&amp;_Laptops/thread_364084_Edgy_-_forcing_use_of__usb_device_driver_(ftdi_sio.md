---
title: "Edgy - forcing use of  usb device driver (ftdi_sio)"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by shotgunefx on 2007-02-17
Hi all,

I'm running  Edgy on my carpc and am having a little problem.

I've got a Tactrix OpenPort cable for ecu tuning/logging, but I can't get the driver to work. It doesn't recognize the device as being associated with ftdi_sio.

It looks like in 2.6.18, this has been fixed, but I'm really not wanting to do another upgrade. I've had hell getting my setup as far as I have due to various dependency issues for the software/hardware I'm using. It being a docked laptop isn't helping.

Is there a way to just tell udev to use the ftdi_sio driver? 

Here's the device info.
> 
Bus 004 Device 010: ID 0403:cc48 Future Technology Devices International, Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0xcc48
  bcdDevice            6.00
  iManufacturer           1 Tactrix
  iProduct                2 OpenPort 1.3 Mitsubishi
  iSerial                 3 TX35188m
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
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 OpenPort 1.3 Mitsubishi
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



Thanks,
-Lee

---

### Post by shotgunefx on 2007-02-18
Well, just said hell with it and went to 2.6.20 and it works fine.

Still curious for reference if there's a way to do that though.

---

