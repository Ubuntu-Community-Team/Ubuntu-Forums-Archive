---
title: "Trouble with mp3 player"
date: 2011-03-10
forum: Hardware
---

### Post by HowlingMad on 2011-03-10
Hi

Using Ubuntu 10.10 on acer aspire laptop.

Trouble - mp3 player (Maplin A32QJ) won't show up on desktop. Works ok on windows without driver, however copying files screws up the order - 1,10,11,12,2,3,4 etc.

Thought this might be a problem that could be solved using usb_modeswitch but not too sure exactly how that works.

Heres the output from lsusb:

```

Bus 001 Device 009: ID 0402:7108 ALi Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0402 ALi Corp.
  idProduct          0x7108 
  bcdDevice            0.02
  iManufacturer           3 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16

```Grateful for any help,

HM

---

### Post by HowlingMad on 2011-03-14
Brushing aside the voluminous offers of help and solidarity I am resigned to using Windows 7 for this purpose.

Only theres one problem: tags that have been written by Sound Juicer do not translate to windows media player. I thought this was a Linux thing, but downloading an album from Ubuntu one store the tags show up fine both in WMP and the Maplin Mp3 player. Even once I had re-entered all my track data into WMP this does not show up on the player.

What gives?

HM

---

### Post by HowlingMad on 2011-03-14
Sorry, thats not entirely true - the Album field shows up on the player, but nothing else. 

HM

---

