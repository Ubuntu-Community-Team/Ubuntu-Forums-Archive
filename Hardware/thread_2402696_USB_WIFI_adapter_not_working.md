---
title: "USB WIFI adapter not working"
date: 2018-10-03
forum: Hardware
---

### Post by mmx21st on 2018-10-03
Hi guys,

I need help with usb Marvell WIFI adapter
command "***lshw -C network***" does not display any info for it.

Output from "***lshw***" shows that the device is UNCLAIMED

...
                 *-usb:1 UNCLAIMED
                      description: Generic USB device
                      product: Marvell Wireless Device
                      vendor: Marvell
                      physical id: 2
                      bus info: usb@1:8.2
                      version: 40.00
                      serial: 0000000000000000
                      capabilities: usb-2.00
                      configuration: maxpower=500mA speed=480Mbit/s
...

Info for the system:
[I][B]
lsb_release -a[/B][/I]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

***uname -r***
4.15.0-20-generic


***lsusb -v -d 1286:2045***
Bus 001 Device 005: ID 1286:2045 Marvell Semiconductor, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1286 Marvell Semiconductor, Inc.
  idProduct          0x2045 
  bcdDevice           40.00
  iManufacturer           1 Marvell
  iProduct                2 Marvell Wireless Device
  iSerial                 3 0000000000000000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Wireless LAN Configuration
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Wireless LAN Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

***modinfo mwifiex_usb***
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/marvell/mwifiex/mwifiex_usb.ko
firmware:       mrvl/usbusb8997_combo_v4.bin
firmware:       mrvl/usb8801_uapsta.bin
firmware:       mrvl/usb8797_uapsta.bin
firmware:       mrvl/usb8766_uapsta.bin
license:        GPL v2
version:        1.0
description:    Marvell WiFi-Ex USB Driver version1.0
author:         Marvell International Ltd.
srcversion:     D40D68B9714271E120D0951
alias:          usb:v1286p204Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1286p2052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1286p204Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1286p2049d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1286p2044d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1286p2043d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1286p2042d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1286p2041d*dc*dsc*dp*ic*isc*ip*in*
depends:        mwifiex
retpoline:      Y
intree:         Y
name:           mwifiex_usb
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

***apt list --installed | grep linux-firmware****

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-firmware/bionic-updates,now 1.173.1 all [installed,automatic]

---

