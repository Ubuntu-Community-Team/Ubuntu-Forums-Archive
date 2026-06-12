---
title: "Trying to get CDC ACM serial device (GRE PSR-800 radio) working"
date: 2011-06-24
forum: Hardware
---

### Post by emf1123 on 2011-06-24
Hi, i'm trying to add support for the cdc_acm serial device in the GRE PSR-800 radio scanner under Ubuntu 10.10.    I'm getting the typical "error -22" failure.

I have added the following stanza to drivers/usb/class/cdc-acm.c and recompiled the module:
            { USB_DEVICE(0x0c97, 0x0008), .driver_info = NOT_A_MODEM, },

when I modprobe the module, i get the following debug messages:
[ 2748.287683] cdc_acm: probe of 2-1:1.1 failed with error -22
[ 2748.288589] usbcore: registered new interface driver cdc_acm
[ 2748.288591] cdc_acm: v0.26-emf:USB Abstract Control Model driver for USB modems and ISDN adapters

I don't know what to do next.  GRE support assures me this is a cdc acm serial device, and it does work as one on windows. 

lsusb:

Bus 002 Device 002: ID 0c97:0008  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0c97 
  idProduct          0x0008 
  bcdDevice            0.01
  iManufacturer           1 GRECOM
  iProduct                2 GRECOM PSR-8OO  Scanner
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           89
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          2 GRECOM PSR-8OO  Scanner
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
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
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
        ** UNRECOGNIZED:  08 11 01 02 02 02 01 00
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      CDC Header:
        bcdCDC               1.10
      CDC ACM:
        bmCapabilities       0x02
          line coding and serial state
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      CDC Call Management:
        bmCapabilities       0x00
        bDataInterface          1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

usb-devices info:
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0c97 ProdID=0008 Rev= 0.01
S:  Manufacturer=GRECOM
S:  Product=GRECOM PSR-8OO  Scanner
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 3 Cls=02(comm.) Sub=02 Prot=01 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=2ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

---

### Post by emf1123 on 2011-06-25
It's closer to working (but still, not working) on Ubuntu 11.04 with kernel 2.6.38-8 and the g_serial usb gadget driver.


[  632.647339] dummy_hcd dummy_hcd: USB Host+Gadget Emulator, driver 02 May 2005
[  632.647344] dummy_hcd dummy_hcd: Dummy host controller
[  632.647781] dummy_hcd dummy_hcd: new USB bus registered, assigned bus number 3
[  632.670578] hub 3-0:1.0: USB hub found
[  632.670583] hub 3-0:1.0: 1 port detected
[  632.672971] g_serial gadget: Gadget Serial v2.4
[  632.672974] g_serial gadget: g_serial ready
[  632.990261] usb 3-1: new high speed USB device using dummy_hcd and address 2
[  633.220165] g_serial gadget: high speed config #2: CDC ACM config
[  633.240205] cdc_acm 3-1:2.0: This device cannot do calls on its own. It is not a modem.
[  633.240234] cdc_acm 3-1:2.0: ttyACM0: USB ACM device
[  652.640183] dummy_hcd dummy_hcd: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.

---

