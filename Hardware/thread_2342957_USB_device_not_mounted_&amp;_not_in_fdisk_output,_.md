---
title: "USB device not mounted &amp; not in fdisk output, but is in lsusb &amp; dmesg"
date: 2016-11-11
forum: Hardware
---

### Post by aeronutt on 2016-11-11
I've searched and looked, but to no avail. I can't figure out what to do with this USB device and 16.04.
Many other USB devices will auto-mount just fine.

dmesg and lsusb recognize device. 
fdisk, disks, gparted, etc do not show a USB device.

Here's what I get:

uname -r
```

4.4.0-43-generic

```

sudo lsusb -v -s 003:003
```


Bus 003 Device 003: ID 11cc:0101  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass          220 Diagnostic
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x11cc 
  idProduct          0x0101 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x60
      (Missing must-be-set bit!)
      Self Powered
      Remote Wakeup
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       220 Diagnostic
      bInterfaceSubClass    160 
      bInterfaceProtocol    176 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered
[~] $ 

```

sudo dmesg
```
[  634.300852] usb 3-4: new full-speed USB device number 4 using xhci_hcd
[  634.430308] usb 3-4: New USB device found, idVendor=11cc, idProduct=0101
[  634.430317] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  634.430588] usb 3-4: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[  634.430603] usb 3-4: ep 0x1 - rounding interval to 1024 microframes, ep desc says 2040 microframes

```

---

### Post by aeronutt on 2016-11-13
Any guidance?

---

### Post by aeronutt on 2017-10-23
I'm back to this. I'd really like to get Ubuntu to discover this device, so I can then use in a virtualbox image of Windows.
Nothing much has changed from above, other than I'm now on 17.04.

Any guidance to getting this USB device to be mountable?

---

### Post by efflandt on 2017-10-23
Do you have any idea what type of USB device it is (memory stick, memory card reader, or ?) and does it work in any other OS (Windows)? From "fdisk, disks, gparted, etc" I assume it is some sort of usb-storage. If it is an older Android phone or something you might need to use settings on the phone itself to put it into usb-storage mode. Newer Android phones use MTP (media trandfer or transport protocal) and would show more info in dmesg.

Is the device listed when you run **lsusb**? This is an example of a usb-storage device (memory stick):```
Bus 002 Device 014: ID 154b:00d4 PNY
```

This is an example of what dmesg shows for a USB memory stick. The **dmesg** command does not require sudo, I typically use **dmesg | less**, so I can scroll through it. Note that Linux assigns this as an "s" device which in this case is sg (due to 2 drives and 4 slot internally USB connected card reader) and the only partition on it is sg1:```
[845949.711479] usb 2-1.4: new high-speed USB device number 14 using ehci-pci
[845950.132541] usb 2-1.4: New USB device found, idVendor=154b, idProduct=00d4
[845950.132545] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[845950.132548] usb 2-1.4: Product: USB 2.0 FD
[845950.132550] usb 2-1.4: Manufacturer: PNY
[845950.132552] usb 2-1.4: SerialNumber: 070B68E404A8F432
[845950.132898] usb-storage 2-1.4:1.0: USB Mass Storage device detected
[845950.133377] scsi host7: usb-storage 2-1.4:1.0
[845951.869808] scsi 7:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 6
[845951.870729] sd 7:0:0:0: Attached scsi generic sg7 type 0
[845951.871860] sd 7:0:0:0: [sdg] 121012224 512-byte logical blocks: (62.0 GB/57.7 GiB)
[845951.872475] sd 7:0:0:0: [sdg] Write Protect is off
[845951.872478] sd 7:0:0:0: [sdg] Mode Sense: 23 00 00 00
[845951.873068] sd 7:0:0:0: [sdg] No Caching mode page found
[845951.873071] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[845951.880102]  sdg: sdg1
[845951.883402] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[845954.359808] FAT-fs (sdg1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
```The fact that Ubuntu does not identify the brand name of your device and only provides ID may be because Linux does not recognize the device```
Bus 002 Device 014: ID 154b:00d4 PNY 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x154b PNY
  idProduct          0x00d4 
  bcdDevice            1.00
  iManufacturer           1 PNY
  iProduct                2 USB 2.0 FD
  iSerial                 3 070B68E404A8F432
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
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
```The unknown device you have only uses 2 mA max and says "Self Powered" vs. this memory stick that uses 300 mA max and is "(Bus Powered)". It is possible that you need to add a udev rule for Linux to recognize it if not a common device. But for anyone to help you, they would need more specifics about what kind of device it is.

---

### Post by aeronutt on 2017-10-25
Thanks for the help.
It's a GPS/sensor data collection device for automotive use (speed, latteral/long G's, time, etc), made by AiM sportline. The file types are proprietary to AiM.  They are relatively small files (a few Mb's each). Not sure of total size of memory on the device.
The good news, I assume because lsusb sees it, I can see the device in my virtual guest image of WIndows10 ! It's recognized there (in the W10 virtual image) by the driver provided by AiM.

Ideally, I'd still like to be able to download the data in linux.

How would I go about adding a udev rule?

---

