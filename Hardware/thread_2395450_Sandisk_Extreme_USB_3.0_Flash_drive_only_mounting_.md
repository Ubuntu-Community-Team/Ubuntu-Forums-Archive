---
title: "Sandisk Extreme USB 3.0 Flash drive only mounting as USB 2.1"
date: 2018-07-02
forum: Hardware
---

### Post by hkphooey on 2018-07-02
So I thought it was time to buy a new USB flash drive, and went for a USB 3.0 one to take advantage of the USB 3.0 port on my laptop. I did some research and came up with this model for a good price performance bet. Great benchmarks and under USD 20. There were options for under 10 USD, but they didn't have great performance, so I paid a bit more. I also got it from the official SanDisk store on my local Eshop, to make sure it wasn't a counterfeit. 

So of course when it arrived I ripped off the package, jammed it in my laptop and copied a few files ... and was immediately disappointed. No faster than my previous USB 2 drives! 

The problem was quickly found ... 
```
lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/7p, 480M
    |__ Port 1: Dev 11, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 3: Dev 3, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
    |__ Port 4: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 4: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 5: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 5: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M

> lsusb -s 1:11
Bus 001 Device 011: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive

```

So yes, although the disk is USB 3, its only mounted as USB 2. (480M). Some more detailed information:

```
sudo lsusb -s 1:11 -v
Bus 001 Device 011: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5580 SDCZ80 Flash Drive
  bcdDevice            0.10
  iManufacturer           1 SanDisk
  iProduct                2 Extreme
  iSerial                 3 AA0107161414424xxxxx
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
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
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
        bInterval              20
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              20
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           7 micro seconds
    bU2DevExitLat         101 micro seconds
Device Status:     0x0000
  (Bus Powered)

```
Its in the USB 3 socket. Its using the xhci_hcd driver. Why am I only getting 480M speed? 

I've been running Linux for 15 years, so I can generally figure stuff out. But I can't find any hints on the Internet about this one. The drive has been around for several years. Its not new hardware. Running Ubuntu Mate 18.04 on this laptop. Where to start ....

---

### Post by hkphooey on 2018-07-02
OK, some  more information. If I reboot the computer with the USB stick in the drive, it comes back up mounted as USB 3, full speed. 
```

~$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/7p, 480M
    |__ Port 3: Dev 2, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
    |__ Port 4: Dev 3, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 4: Dev 3, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 5: Dev 4, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 5: Dev 4, If 1, Class=Video, Driver=uvcvideo, 480M


:~$ sudo lsusb -s 2:2 -v

Bus 002 Device 002: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5580 SDCZ80 Flash Drive
  bcdDevice            0.10
  iManufacturer           1 SanDisk
  iProduct                2 Extreme
  iSerial                 3 AA010716141442467617
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           44
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
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           7 micro seconds
    bU2DevExitLat         101 micro seconds
Device Status:     0x000c
  (Bus Powered)
  U1 Enabled
  U2 Enabled

```
Its in exactly the same slot, but it swaps over to the correct USB bus. How can that happen? Obviously I don't want to have to reboot the computer every time I insert the USB drive. 
I've tested the speeds, all good when plugged as it is. If I remove it and re-insert it mounts on the wrong Bus and drops back to USB 2 speeds.

---

### Post by miltonlai on 2019-01-21
The same issue happens when I am using a UNITEK sd card reader on my ThinkPad X240. In both USB3.0 sockets it was recognized as bcdUSB 2.1
I didn't try the reboot thing but I found another solution, if I plug it to a 4-port USB3 hub, then plug the hub to X240, it can be recognized as bcdUSB 3.0.
It's weird.

---

