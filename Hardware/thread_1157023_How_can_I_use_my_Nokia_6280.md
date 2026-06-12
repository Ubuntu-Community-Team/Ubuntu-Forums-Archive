---
title: "How can I use my Nokia 6280"
date: 2009-05-12
forum: Hardware
---

### Post by albertz on 2009-05-12
I plugged it in via USB and I expected to get access to the files. But nothing showed up.

This is lsusb -v:

Bus 002 Device 010: ID 0421:045b Nokia Mobile Phones 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0421 Nokia Mobile Phones
  idProduct          0x045b 
  bcdDevice            5.53
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                8mA
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
        bInterval               0
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
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


What do I need?

---

### Post by Macchi on 2009-05-12
I can access the files on a couple of Nokia phones via Bluetooth on Ubuntu 9.04. Of course you have to pair the devices. File communication over bluetooth is slow, but it works.

As I understand, The connection through a USB cable depends on having udev rules that work with your specific devices. Is this correct? Maybe the 6280 is not in the udev database?

Have you tried the command dmesg after insertion of the USB cable?

---

### Post by albertz on 2009-05-12
That computer does not have bluetooth.

When I plugged it in on Windows, a new drive did pop up, in a similar way when I plug in an USB stick.

Do I have to install special drivers to be able to access the files on my Nokia in Ubuntu? Where can I get those?

---

### Post by Macchi on 2009-05-12
Some people reported a method to solve the problem:
[http://ubuntuforums.org/showthread.php?t=975622&page=4](http://ubuntuforums.org/showthread.php?t=975622&page=4)



You don't have to install new drivers, but the existing drivers in the linux kernel have to be told how to access your Nokia device (throught so called udev rules).
Unfortunately many equipment manufacturers still ignore to provide solutions or documentation to make the devices work on GNU/Linux and Mac OS X.

---

### Post by albertz on 2009-05-12
Thanks for the hint. I feel a bit ashamed that I didn't found that one myself...

---

### Post by Cruncher on 2009-08-03
As a matter of fact, the automatic registration of the 6280 as a SCSI disk worked fine before 9.04, without any manual configuration. But after my upgrade to 9.04 it stopped working.

EDIT: Woops, actually the problem was, that I did do the mentioned changes sometime in the past, but the upgrade to 9.04 erased those files :-D

---

