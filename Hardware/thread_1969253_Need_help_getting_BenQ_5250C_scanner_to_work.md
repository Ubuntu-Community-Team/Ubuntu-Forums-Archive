---
title: "Need help getting BenQ 5250C scanner to work"
date: 2012-04-29
forum: Hardware
---

### Post by adrianpang on 2012-04-29
Hello,

I have a BenQ 5250C scanner, which works fine under Windows, but I can't get it to work on my Ubuntu 12.04 system.  Here's what I have tried so far:

1) download the latest driver for the scanner from BenQ's site
2) extract bin/u55v009.bin from the zip, and copied it to /etc/sane.d
3) chmod the file to 777
4) edit /etc/sane.d/snapscan.conf such that 
firmware /etc/sane.d/u55v009.bin is in the file
5) plugin in the scanner.

Running scanimage -L displays
device `snapscan:libusb:001:007' is a Acer FlatbedScanner40 flatbed scanner

However, running just scanimage (even as root) gives:
scanimage: open of device snapscan:libusb:001:007 failed: Error during device I/O

Here's the output of lsusb -v.  Can someone give me a hand setting this up?

Bus 001 Device 007: ID 04a5:2137 Acer Peripherals Inc. (now BenQ Corp.) Benq 5150/5250
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x04a5 Acer Peripherals Inc. (now BenQ Corp.)
  idProduct          0x2137 Benq 5150/5250
  bcdDevice            1.10
  iManufacturer           1 BenQ 
  iProduct                2 Color FlatbedScanner 36
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              16
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

---

