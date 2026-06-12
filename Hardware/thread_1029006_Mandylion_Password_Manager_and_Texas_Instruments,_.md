---
title: "Mandylion Password Manager and Texas Instruments, Inc. TUSB3410 Microcontroller pains"
date: 2009-01-02
forum: Hardware
---

### Post by ragelink on 2009-01-02
So I bought a Mandylion password manager about a year ago... I love it and because I had to use a windows distro at work I didn't really mind that the software only came for windows. I switched jobs and now I have a choice, so I ditched the windows and went all Linux (ubuntu whatever latest and stable I can have) :D

I loaded up some drivers and seems to be doing ok in terms of the machine seeing the device however this is what comes out of dmsesg whenever I plug it in.

[  318.593760] usb 5-2: USB disconnect, address 2
[  322.898883] usb 5-2: new full speed USB device using uhci_hcd and address 3
[  323.089847] usb 5-2: configuration #1 chosen from 1 choice
[  323.093755] ti_usb_3410_5052: probe of 5-2:1.0 failed with error -5
[ 1249.597928] usb 6-2.1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110

I am here because I dunno what else to do. If anyone has any pointers on getting this to work pls let me know.

Googling gets me to the same issues with other devices but not a fox so far.

The device is picked up by lsusb but i have no /dev/ttyUSBx to do anything with it. I was able to install the software via WINE but I still need to be able to talk to the device so I figured if I could get serial USB to point to some /dev/ttyUSBx I can then redirecto to a COM port or something.

Thanks for helping out or at least reading this.


root@system:~# lsusb
Bus 006 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

This is what an lsusb -v prints for this particular device

root@system:~# lsusb
Bus 005 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x3410 TUSB3410 Microcontroller
  bcdDevice            1.00
  iManufacturer           1 Texas Instruments
  iProduct                2 TUSB3410 Boot Device
  iSerial                 3 TUSB3410        
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

-some other notes the driver I'm using was built for kernel 2.6.11 but I'm on 2.6.27-server (so I can has 4 GBS of RAM-tabulous performance)
ti_usb_3410_5052.ko is the driver.

BTW Ubuntu community I love you... Ive been using the forums for years but this is the first time that I've had to post as usually just searching for stuff gives me the answers I need. I sincerely hope someone will be able to point me in the right path.

-RageLink

---

### Post by ragelink on 2009-01-02
Restarted and pluged in the device now I get.

[  329.000207] usb 6-2: USB disconnect, address 2
[  332.160114] usb 6-2: new full speed USB device using uhci_hcd and address 3
[  332.415387] usb 6-2: configuration #1 chosen from 1 choice
[  332.540207] ti_usb_3410_5052: disagrees about version of symbol struct_module

interesting if I find anything else.

root@system:~$ lsusb -vs 006:003

Bus 006 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x3410 TUSB3410 Microcontroller
  bcdDevice            1.00
  iManufacturer           1 Texas Instruments
  iProduct                2 TUSB3410 Boot Device
  iSerial                 3 TUSB3410        
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

---

