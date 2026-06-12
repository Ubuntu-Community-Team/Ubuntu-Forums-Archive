---
title: "USB 3 Storage detected but non functional"
date: 2015-03-28
forum: Hardware
---

### Post by mobodo on 2015-03-28
I have a USB 3 device which works well on MacOS X but won't mount on Ubuntu.  This is on a fresh install of 14.04 Desktop.

The USB 3 appears to be working on the host:

Output from **lspci**:
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
**02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)**

```

The system picks it up when it is plugged in - **dmsg** gives:
```

[ 6624.074483] usb 4-1: new SuperSpeed USB device number 19 using xhci_hcd
[ 6624.096279] usb 4-1: New USB device found, idVendor=1e91, idProduct=a1a2
[ 6624.096284] usb 4-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 6624.096286] usb 4-1: Product: Envoy 2012
[ 6624.096289] usb 4-1: Manufacturer: OWC
[ 6624.096291] usb 4-1: SerialNumber: 0000000000000000002B
[ 6624.099600] scsi7 : uas
[ 6624.100020] scsi 7:0:0:0: Direct-Access     Envoy    2012             0    PQ: 0 ANSI: 6
[ 6624.100585] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 6624.100730] sd 7:0:0:0: [sde] Spinning up disk...
[ 6625.102425] ...........................................................................................not responding...
[ 6745.591550] sd 7:0:0:0: [sde] READ CAPACITY(16) failed
[ 6745.591555] sd 7:0:0:0: [sde]  
[ 6745.591558] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6745.591560] sd 7:0:0:0: [sde]  
[ 6745.591562] Sense Key : Not Ready [current] 
[ 6745.591566] sd 7:0:0:0: [sde]  
[ 6745.591568] Add. Sense: Logical unit is in process of becoming ready
[ 6766.578606] sd 7:0:0:0: [sde] READ CAPACITY failed
[ 6766.578611] sd 7:0:0:0: [sde]  
[ 6766.578614] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6766.578616] sd 7:0:0:0: [sde]  
[ 6766.578618] Sense Key : Not Ready [current] 
[ 6766.578621] sd 7:0:0:0: [sde]  
[ 6766.578624] Add. Sense: Logical unit is in process of becoming ready
[ 6787.566220] sd 7:0:0:0: [sde] Test WP failed, assume Write Enabled
[ 6794.561876] sd 7:0:0:0: [sde] Asking for cache data failed
[ 6794.561882] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 6794.562851] sd 7:0:0:0: [sde] Spinning up disk...
**[ 6795.565085] ...........................................................................................not responding...**
[ 6916.061092] sd 7:0:0:0: [sde] **READ CAPACITY(16) failed**
[ 6916.061097] sd 7:0:0:0: [sde]  
[ 6916.061100] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6916.061102] sd 7:0:0:0: [sde]  
[ 6916.061104] Sense Key : Not Ready [current] 
[ 6916.061107] sd 7:0:0:0: [sde]  
[ 6916.061110] Add. Sense: Logical unit is in process of becoming ready
[ 6937.046461] sd 7:0:0:0: [sde] **READ CAPACITY failed**
[ 6937.046467] sd 7:0:0:0: [sde]  
[ 6937.046469] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6937.046471] sd 7:0:0:0: [sde]  
[ 6937.046473] Sense Key : Not Ready [current] 
[ 6937.046477] sd 7:0:0:0: [sde]  
[ 6937.046479] Add. Sense: Logical unit is in process of becoming ready
[ 6965.026682] sd 7:0:0:0: [sde] Attached SCSI disk

```


The USB drive is detected - output from **lsusb -v**:

```

(...)

Bus 004 Device 019: ID 1e91:a1a2  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x1e91 
  idProduct          0xa1a2 
  bcdDevice            1.00
  iManufacturer           2 OWC
  iProduct                3 Envoy 2012
  iSerial                 1 0000000000000000002B
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          121
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
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
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           4
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     98 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
        MaxStreams             16
        Data-in pipe (0x03)
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
        MaxStreams             16
        Data-out pipe (0x04)
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
        MaxStreams             16
        Status pipe (0x02)
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               0
        Command pipe (0x01)
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat          10 micro seconds
    bU2DevExitLat        2047 micro seconds
Device Status:     0x0001
  Self Powered


```

It is associated as a scsi device under /dev/sde - output from **lshw**:
```

(...)
     *-scsi:4
          physical id: 6
          bus info: usb@4:1
          logical name: scsi7
        *-disk
             description: SCSI Disk
             product: 2012
             vendor: Envoy
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sde
             version: 0
             serial: B2000000000000000000
             configuration: ansiversion=6 sectorsize=512

```

I cannot do anything with /dev/sde in dfisk or parted.  If anyone has an idea how I could get this USB 3 external drive to work under Ubuntu, I would appreciate.

---

### Post by weatherman2 on 2015-03-28
This is a fresh install of Ubuntu 14.04.2 plus with all the latest updates?

Do you have any USB 2.0 ports?  Does the drive work when plugged into one of those USB 2.0 ports?

---

