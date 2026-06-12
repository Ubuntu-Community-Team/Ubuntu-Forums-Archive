---
title: "empia em28xx driver problems"
date: 2011-05-14
forum: Hardware
---

### Post by ultimbro on 2011-05-14
Hi, I'm pretty new to ubuntu , I just dumped my win7

I have a usb TV tuner stick with empia chip
I tried to install driver as it's shows on linuxtv.org

but when I do the "make" part I got an error :

[I]/home/phil/v4l-dvb/v4l-dvb/v4l/flexcop-i2c.c: In function 'flexcop_i2c_init':
/home/phil/v4l-dvb/v4l-dvb/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)
/home/phil/v4l-dvb/v4l-dvb/v4l/flexcop-i2c.c:253:39: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/phil/v4l-dvb/v4l-dvb/v4l/flexcop-i2c.o] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [_module_/home/phil/v4l-dvb/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/phil/v4l-dvb/v4l-dvb/v4l'
make: *** [all] Error 2
[/I]

and here's my lsusb report  for this device: 

Bus 001 Device 002: ID eb1a:1111 eMPIA Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0xeb1a eMPIA Technology, Inc.
  idProduct          0x1111 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
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
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ac  1x 940 bytes
        bInterval               1



I would need some help here, if it were windows I would be able to do something but here in ubuntu, I'm a newbie!


Thanks a lot !

---

