---
title: "Nokia C-15"
date: 2009-12-08
forum: Hardware
---

### Post by AntonJ on 2009-12-08
Hi everyone, 

I have bought Nokia C-15 mobile modem, or so called internet stick and I have googled for 3 days to find solution, but I could not find solution. My problem:
1) When I insert C-15 in to laptop, Happens nothing. I mean no visible reaction from Ubuntu and no red/green light on my C-15.
2) I have tried to insert string from here [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=1355&sid=c67856fe4c244a23614eaf8d4a8d2d84](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=1355&sid=c67856fe4c244a23614eaf8d4a8d2d84) to make it work, I have had a look on ZeroCD - no DEB packages, no nothing.
Actually at the moment I have no clue.

Could any one help me?[URL="http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=1355&sid=c67856fe4c244a23614eaf8d4a8d2d84"]
[/URL]

---

### Post by AntonJ on 2009-12-08
If you do not have the solution, then maybe you can give me advice who should I ask?

---

### Post by AntonJ on 2009-12-10
So no ideas .... that is bad...

For a while I'll try to force that Modem recognizing By Ubuntu, do not know how long I'll have sufficient interest in that....

there is my "sudo lsusb -s002: -v" command result ("-s002:" option shows, which but to scan, if you do not know your device Bus number, type  "sudo lsusb -v")
> 
Bus 002 Device 004: ID 0421:0610 Nokia Mobile Phones 
Device Descriptor:
..bLength                18
..bDescriptorType         1
..bcdUSB               2.00
..bDeviceClass            0 (Defined at Interface level)
..bDeviceSubClass         0 
..bDeviceProtocol         0 
..bMaxPacketSize0        64
..idVendor           0x0421 Nokia Mobile Phones
..idProduct          0x0610 
..bcdDevice            0.01
..iManufacturer           2 Nokia
..iProduct                1 Nokia Datacard
..iSerial                 3 0.0.1
..bNumConfigurations      1
..Configuration Descriptor:
....bLength                 9
....bDescriptorType         2
....wTotalLength           32
....bNumInterfaces          1
....bConfigurationValue     1
....iConfiguration          0 
....bmAttributes         0x80
......(Bus Powered)
....MaxPower              500mA
....Interface Descriptor:
......bLength                 9
......bDescriptorType         4
......bInterfaceNumber        0
......bAlternateSetting       0
......bNumEndpoints           2
......bInterfaceClass         8 Mass Storage
......bInterfaceSubClass      6 SCSI
......bInterfaceProtocol     80 Bulk (Zip)
......iInterface              0 
......Endpoint Descriptor:
........bLength                 7
........bDescriptorType         5
........bEndpointAddress     0x01  EP 1 OUT
........bmAttributes            2
..........Transfer Type            Bulk
..........Synch Type               None
..........Usage Type               Data
........wMaxPacketSize     0x0200  1x 512 bytes
........bInterval               0
......Endpoint Descriptor:
........bLength                 7
........bDescriptorType         5
........bEndpointAddress     0x81  EP 1 IN
........bmAttributes            2
..........Transfer Type            Bulk
..........Synch Type               None
..........Usage Type               Data
........wMaxPacketSize     0x0200  1x 512 bytes
........bInterval               0
Device Qualifier (for other device speed):
..bLength                10
..bDescriptorType         6
..bcdUSB               2.00
..bDeviceClass            0 (Defined at Interface level)
..bDeviceSubClass         0 
..bDeviceProtocol         0 
..bMaxPacketSize0        64
..bNumConfigurations      1
Device Status:     0x0000
..(Bus Powered)

Later I am planing to find USB device diagnostic tool, to have a look, is there any USB failures.

---

