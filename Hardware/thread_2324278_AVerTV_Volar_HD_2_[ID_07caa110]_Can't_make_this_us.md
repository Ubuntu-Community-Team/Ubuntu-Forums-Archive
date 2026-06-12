---
title: "AVerTV Volar HD 2 [ID: 07ca:a110] Can't make this usable on Linux?"
date: 2016-05-12
forum: Hardware
---

### Post by Portaro on 2016-05-12
There is my problem here:
I Buy this usb to connect and see TV on PC, but I cant make this usable on 14.04&#8594;

```
Device: ID 07ca:a110 AVerMedia Technologies, Inc. Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07ca AVerMedia Technologies, Inc.
  idProduct          0xa110 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
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
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0



```

I also try this &#8594; [https://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](https://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
[https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#AVerMedia_AVerTV_A800](https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#AVerMedia_AVerTV_A800)

There is possible configure this device on GNU/Linux or not?

Any Idea .

---

### Post by Portaro on 2016-05-12
Ok I think that this way can work  &#8594; [https://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](https://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Only problem that I see is that the driver is used to cover the device is Afatech AF9033 

[[img]http://s25.postimg.org/pt1cncszv/2016_05_12_194221_1280x1024_scrot.jpg[/img]](http://postimg.org/image/pt1cncszv/)

Maybe this can work for  others.

First 
git clone git://linuxtv.org/media_build.git

Then move on terminal to the result directory of down 

cd media_build

Then use launch the script inside called :
 ./build

This take some time to build

When is finished simply do a **sudo make install**  and all corrections and drivers can be now applyed to the kernel in my case I use
 3.13.0-49-generic

I think that this way can active  the AVerTV Volar HD 2 with cover fucntion of driver with Afatech AF9033 in my case and the device is recognized &#8594;
> [691][joao:/home/joao]$ ls /dev/dvb
adapter0
[692][joao:/home/joao]$ 

Final I suggest the use of MeTV software to see if the device appear or not, because I use Kaffeine and I cant see the device (or Im not understand where is the option to do this on the Kaffeine! I dont know very well this type of programs!sorry)  .But When I open MeTV the device is listed , I think is more easy on MeTV to see the device, and the  search options -  also like the process of search  of channels , on Kaffeine is less intuitive .
You can install MeTV with &#8594; sudo apt-get install me-tv.

Maybe can work for you.:popcorn:

---

