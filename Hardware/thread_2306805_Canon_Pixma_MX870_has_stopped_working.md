---
title: "Canon Pixma MX870 has stopped working"
date: 2015-12-19
forum: Hardware
---

### Post by CelticWhisper on 2015-12-19
I'm having trouble with a Canon Pixma MX870 on 14.04 64-bit.  It was working up until today, when attempting to scan results in a "Scanner is warming up, do not open the document cover" notice followed by a long delay and a "Cannot communicate with scanner" message.  It has only ever been attached via USB, never over the (W)LAN.
[ATTACH=CONFIG]266240[/ATTACH]

The scanner shows as bus 008, device 003 in the initial Scangearmp dialog box, but clicking "Update scanner list" results in a neverending progress dialog.  Clicking "Cancel" freezes the window and I have to kill the PID to close scangear.  
[ATTACH=CONFIG]266241[/ATTACH]

I have attempted to attach the device to a VirtualBox VM running Windows 7, but scans inside the guest VM return the same ScanGear error.
[ATTACH=CONFIG]266242[/ATTACH]
[ATTACH=CONFIG]266243[/ATTACH]

Following suggestions I've read from other posts and forums, I've run lsusb and dpkg -l as root to gather some informaton.

Output from lsusb -v is here:
```
Bus 008 Device 003: ID 04a9:1743 Canon, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04a9 Canon, Inc.
  idProduct          0x1743 
  bcdDevice            0.01
  iManufacturer           1 Canon
  iProduct                2 MX870 series
  iSerial                 3 30A8B0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              11
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8b  EP 11 IN
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

```


Output from sudo dpkg -l | grep scangear is here (note that this is after a few [un|re]installs of packages in an effort to resolve the issue):
```
sudo dpkg -l | grep scangear

ii  scangearmp-common                                     2.10-33~raring1                                     i386         ScanGear MP for Linux.
ii  scangearmp-common-32                                  2.10-33~raring1                                     amd64        ScanGear MP for Linux.
ii  scangearmp-mx870series                                2.10-33~raring1                                     i386         ScanGear MP for Linux.
ii  scangearmp-mx870series-32                             2.10-33~raring1                                     amd64        ScanGear MP for Linux.

```

I have verified that the device works when connected to another physical host (laptop running Windows 8.1 64-bit, using drivers from Canon's website), so I suspect the problem is somehow USB bus-related.  I just don't know enough about tracking down USB connectivity issues to A. say with 100% certainty and B. figure out how to actually fix it.  I've tried the device in two different (onboard, not front-panel) ports with it (the device) showing up as 002 and 003 on the same bus (008) but neither way has yielded any results.

The primary user of the Ubuntu host is not a sysadmin, so it's highly unlikely they installed or changed any packages that would have broken compatibility.  The system is, however, configured to auto-install security updates.

Can I get some guidance on how to restore this scanner?  Muchas gracias.  :)

---

