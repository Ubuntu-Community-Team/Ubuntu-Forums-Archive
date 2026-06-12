---
title: "equinux Tubestick Hybrid ATSC"
date: 2010-05-25
forum: Hardware
---

### Post by roberto.tomas on 2010-05-25
I'm on lucid: 2.6.32-21-powerpc64-smp
what module do I need to get my equinux Tubestick Hybrid ATSC (usb tv-tuner) working? EQ20026 is the part number on the card.

I tried af9015 -- because that is what it *used* to be -- even the manufacturer, and one of the developers of the af9015 driver told me that. Then more recently I read that it was em28xx. Both ofthese I have built and installed. After I had the af9015 installed, the Administration->Hardware detected that I needed a firmware -- I installed that and it looks generally like the firmware for em28xx: xc3028-v27.fw -- then I read on ubuntu-fr that, a year or so ago, there was a different driver I would need, one of the four firmware packages for em28xx, the third one in fact. I have tried all four of them, none work. (this is removing the old firmware, removing the em28xx modules, installing the new firmware, modprobing the em28xx modules back up, and reconnecting the usb tuner). That's a lot of work.

I worked through building af9015 according to the instructions on the english language forums here, and then followed the instructions on ubuntu-it -- neither of those connected my device either.

relavant lsusb -v details:
```
Bus 001 Device 029: ID 1d2c:1012  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1d2c 
  idProduct          0x1012 
  bcdDevice            1.10
  iManufacturer           3 equinux
  iProduct                1 TubeStick Hybrid ATSC
  iSerial                 2 200803
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength        12545
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
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               4
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
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xd40a  3x 1034 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000c  1x 12 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0013  1x 19 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x5c13  (??) 1043 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc413  1x 1043 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0014  1x 20 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xc400  1x 1024 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0xf002  3x 2 bytes
        bInterval               1
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
```

---

### Post by roberto.tomas on 2010-05-28
one of the kind folks over at #ubuntu-kernel helped me build the  em28xx-new  -- the version of em28xx supplied by ubuntu does not support  the Equinux card, but the em28xx-new (from like 3 years ago this  branched off) does.

Here's the basic steps , but mind you this just gets the driver built  and recognizing your card -- I can't yet report full success as I don't  have /dev/dvb, so I can't yet watch tv (not sure why, I read it might b  firmware but ubuntu's hardware gui already detected and installed the  firmware):

1. clean your system from previous build attempts:
```
sudo rm -rf /lib/modules/`uname -r`/empia
sudo mv /lib/modules/`uname -r`/kernel/drivers/media Código/media_backup
sudo apt-get --reinstall install  linux-image-2.6.32-21-powerpc64-smp
```2. get the em28xx-new driver:
```
wget http://launchpadlibrarian.net/35049921/em28xx-new.tar.gz
tar xvfz em28xx-new.tar.gz
cd em28xx-new/
```3. alter the em28xx-i2c.c file, changing line 728  to this:
```
    if (dev->has_inttuner == 1) {
```(just removes one of  the conditions in the if statement)
4. build and install the driver:
```
make clean && make
sudo modprobe -r videodev
sudo make install
```5. run this command in the terminal and remove  and reinsert the card (or just reboot, is safer):
```
tail -f /var/log/messages
```You should get output like this:
```
May 28 14:49:58 quad-g5 kernel: [ 4052.895857] usb 1-2: USB  disconnect, address 11
May 28 14:50:03 quad-g5 kernel: [ 4057.179630] usb 1-2: new high speed  USB device using ehci_hcd and address 12
May 28 14:50:03 quad-g5 kernel: [ 4057.320580] usb 1-2: configuration #1  chosen from 1 choice
May 28 14:50:03 quad-g5 kernel: [ 4057.320822] em28xx: new video device  (2c1d:1210): interface 0, class 255
May 28 14:50:03 quad-g5 kernel: [ 4057.320828] em28xx: device is  attached to a USB 2.0 bus
May 28 14:50:03 quad-g5 kernel: [ 4057.320837] em28xx #0: Alternate  settings: 8
May 28 14:50:03 quad-g5 kernel: [ 4057.320842] em28xx #0: Alternate  setting 0, max size= 0
May 28 14:50:03 quad-g5 kernel: [ 4057.320848] em28xx #0: Alternate  setting 1, max size= 0
May 28 14:50:03 quad-g5 kernel: [ 4057.320853] em28xx #0: Alternate  setting 2, max size= 1448
May 28 14:50:03 quad-g5 kernel: [ 4057.320858] em28xx #0: Alternate  setting 3, max size= 2048
May 28 14:50:03 quad-g5 kernel: [ 4057.320863] em28xx #0: Alternate  setting 4, max size= 2304
May 28 14:50:03 quad-g5 kernel: [ 4057.320868] em28xx #0: Alternate  setting 5, max size= 2580
May 28 14:50:03 quad-g5 kernel: [ 4057.320874] em28xx #0: Alternate  setting 6, max size= 2892
May 28 14:50:03 quad-g5 kernel: [ 4057.320879] em28xx #0: Alternate  setting 7, max size= 3072
May 28 14:50:03 quad-g5 kernel: [ 4057.582953] em28xx #0: found i2c  device @ 0x88 [msp34xx/cx25843]
May 28 14:50:03 quad-g5 kernel: [ 4057.587946] em28xx #0: found i2c  device @ 0xa0 [eeprom]
May 28 14:50:03 quad-g5 kernel: [ 4057.606206] em28xx #0: Found  <NULL>
```

-- from what I've been reading I should be able to install the firmware properly with:
```
sudo mv /lib/firmware/xc3028-v27.fw /lib/firmware/xc3028-v27.fw.old 
--install the em28xx-new driver
wget http://jiemeb.free.fr/pinnacle/cleanEm28xx.sh
chmod +x cleanEm28xx.sh
sudo ./cleanEm28xx.sh
wget http://media.ubuntuusers.de/forum/attachments/1862452/xc3028-v27-1.sh
chmod +x xc3028-v27-1.sh
./xc3028-v27-1.sh
sudo reboot
```
(there are exceptions for other cards so you can't just follow this blindly if you are using a different em28xx card)

---

### Post by roberto.tomas on 2010-06-06
I found out that the em28xx-new drivers that support equinux do not support the ATSC tuner part of the card. since nowhere except maybe some south pacific islands and parts of south america still uses NTSC broadcasts, that's gonna be a problem :P

---

