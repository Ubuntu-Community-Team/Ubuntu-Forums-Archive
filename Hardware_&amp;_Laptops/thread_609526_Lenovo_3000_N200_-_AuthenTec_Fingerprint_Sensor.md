---
title: "Lenovo 3000 N200 - AuthenTec Fingerprint Sensor"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by chrismyers on 2007-11-11
I'd love to get the biometric scanner working on the Lenovo 3000.

Doing some research, I believe that Thinkfinger does not work & I'm not sure wheather Bioapi works.

Has anyone had any success & would they like to share their findings (successful or not)?

Just for the sake of clarification, sudo lsusb -v produces:

Bus 002 Device 004: ID 08ff:2580 AuthenTec, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x08ff AuthenTec, Inc.
  idProduct          0x2580 
  bcdDevice            6.23
  iManufacturer           0 
  iProduct                1 Fingerprint Sensor
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bNumEndpoints           2
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
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

Many thanks.

---

### Post by paviola on 2008-01-05
Got the same problem !
Hope someone has figured it out ?

---

### Post by CazperII on 2008-01-05
[http://ubuntuforums.org/showthread.php?t=650733&highlight=N200](http://ubuntuforums.org/showthread.php?t=650733&highlight=N200)

Look over there, although being alpha software, the driver and software works and I am currently able to login and sudo with the fingerprint reader. 

If you are using a x86 distro the install should be easy, because there are .deb files available. I am using a amd64 distro of Ubuntu and I had to compile from source.

---

