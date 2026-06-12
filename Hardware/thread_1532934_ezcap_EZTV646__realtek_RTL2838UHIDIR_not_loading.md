---
title: "ezcap EZTV646 / realtek RTL2838UHIDIR not loading"
date: 2010-07-17
forum: Hardware
---

### Post by &lt;mike&gt; on 2010-07-17
Hi all,

I'm trying to put together a mythtv box for my sister in law, and have come unstuck trying to install the dvb-t usb stick she bought.

All I get from dmesg is 
```

[  844.600066] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  844.767272] usb 1-1: configuration #1 chosen from 1 choice

```
and lsmod |grep dvb returns nothing at all.

It's branded ezcap, and the product id (on the barcode on the box) is EZTV646 (646?). lsusb returns:


```
$ sudo lsusb -v

Bus 001 Device 007: ID 0bda:2838 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x2838 
  bcdDevice            1.00
  iManufacturer           1 Realtek
  iProduct                2 RTL2838UHIDIR
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 USB2.0-Bulk&Iso
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
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)

```

Has anyone had any luck with this one?
I have tried a number of howtos on the net to do with the Realtek RTL2832u driver, including
[http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/readme.lv5tdlx.txt](http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/readme.lv5tdlx.txt)
and I've tried the new drivers at
[http://www.linuxtv.org/wiki/index.php/Realtek_RTL2831U](http://www.linuxtv.org/wiki/index.php/Realtek_RTL2831U)
but to no avail so far.

Any help would be greatly appreciated

---

### Post by toscal on 2010-09-18
I am having similar problems. 
 I have just written off to the Manufacturers of the stick a company called Forward Video to see if they can help.
Their website is  [_Forward video_]("http://www.szforwardvideo.com")

---

### Post by Wes Baker on 2010-10-26
Hi guys,  I have the same stick and did manage to get in working in Lucid using the howtos you mentioned.  But something has happened now since my last update (I think..I dont use the tuner all that often) and now I am getting the following in my dmesg:

[ 3098.361576] dvb_usb_rtl2832u: disagrees about version of symbol dvb_usb_device_init
[ 3098.361584] dvb_usb_rtl2832u: Unknown symbol dvb_usb_device_init


And sudo modprobe dvb-usb-rtl2832u returns: 

FATAL: Error inserting dvb_usb_rtl2832u (/lib/modules/2.6.32-25-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-rtl2832u.ko): Unknown symbol in module, or unknown parameter (see dmesg)


Easy come easy go I guess, but I'm keen to hear how you guys are getting along...Did sz forward video come back with any response toscal?

---

