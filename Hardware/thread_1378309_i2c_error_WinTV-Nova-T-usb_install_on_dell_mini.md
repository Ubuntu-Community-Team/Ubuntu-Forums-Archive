---
title: "i2c error: WinTV-Nova-T-usb install on dell mini"
date: 2010-01-11
forum: Hardware
---

### Post by craslett on 2010-01-11
I've got a Dell 9 running the supplied Ubuntu 8.04:

Ubuntu 8.04.2
Linux 2.6.24-24-lpia
GNOME 2.22.3 (Ubuntu 2008-07-09)

I've just been given a Hauppage WinTV-Nova-T USB stick Model 294 (SL-294-V2.5-UK)

Installed MeTV and then plugged tyhe gizmo in.

MeTV says "NO TUNER DEVICE".  

Off to ls-usb and logs ...

root@dellmini:/home/dellmini# lsusb
Bus 005 Device 005: ID 2040:7070 Hauppauge 
Bus 005 Device 002: ID 064e:a102 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

root@dellmini:/home/dellmini# lsusb -v (extract for device 5)
Bus 005 Device 005: ID 2040:7070 Hauppauge 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2040 Hauppauge
  idProduct          0x7070 
  bcdDevice            1.00
  iManufacturer           1 Hauppauge
  iProduct                2 Nova-T Stick
  iSerial                 3 4033403914
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1

So the device was seen ... but the logs show a firmware failure??

[ 6927.926226] usb 5-3: new high speed USB device using ehci_hcd and address 12
[ 6928.058577] usb 5-3: configuration #1 chosen from 1 choice
[ 6928.060034] dvb-usb: found a 'Dell Digital TV Receiver' in cold state, will try to load a firmware
[ 6928.090968] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 6928.365606] dib0700: firmware started successfully.
[ 6928.868410] dvb-usb: found a 'Dell Digital TV Receiver' in warm state.
[ 6928.868583] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 6928.869143] DVB: registering new adapter (Dell Digital TV Receiver)
[ 6929.053956] dib0700: i2c write error (status = -32)
[ 6929.053961] 
[ 6929.053976] lgdt3305_read_reg: error (addr 0e reg 0001 error (ret == 0)
[ 6929.053983] lgdt3305_attach: error -121 on line 1059
[ 6929.053988] lgdt3305_attach: unable to detect LGDT3305 hardware
[ 6929.054105] dvb-usb: no frontend was attached by 'Dell Digital TV Receiver'
[ 6929.054114] dvb-usb: Dell Digital TV Receiver successfully initialized and connect

So it appears to have found the latest drivers from /lib/firmware/2.6.24-24-lpia/dvb-usb-dib0700-1.20.fw

Anyone any experience of this ... it says it's an i2c write error ... bus issue?? sounds like firmware?

I'm a newbie to this so any help would be most welcome

---

