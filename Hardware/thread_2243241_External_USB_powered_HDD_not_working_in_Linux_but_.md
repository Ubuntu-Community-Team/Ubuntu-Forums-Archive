---
title: "External USB powered HDD not working in Linux but working in Windows"
date: 2014-09-07
forum: Hardware
---

### Post by KumarAseem on 2014-09-07
I have an external WD My Passport 1TB HDD and it is around 2+ years old. I normally apply the routine upgrades that Kubuntu auto suggests and some were applied 3 days back as well. I hadn't plugged the HDD in from some days so not sure if something in one of those upgrades has caused the issue. The drive works perfectly fine on another machine that is running Windows 7 and also on my laptop when passed to the VM (virtualbox) running windows 7 but it does not work when connected to the base Kubuntu OS. I believe then that the drive, cable and the USB port are fine and this could be some Linux driver/setting issue.

The first time when I connected it today after many days I heard tick tick sounds repeating every 2-3 seconds. I thought something is wrong and immediately unplugged it. I then connected it back to the same port and no sound this time. The drive was vibrating though and the light on it was on (non blinking). I unplugged it and attached it to another port. This time also it did vibrate but nothing showed in the OS. I unplugged and attached to the third port and it took some seconds but the OS properly picked it up and mounted all the partitions (ntfs) in it. I opened the folders and gave the command to create a new folder and the whole drive vanished. It remounted after some seconds. This time I gave the command to paste a file and the drive again vanished. I then re-plugged it (in the same port) and the OS did not mount any partitions. Tried it by plugging it in other ports and no good result. In the dmesg logs it showed this:
```

[    2.432128] usb 6-2: device descriptor read/64, error -71
[    2.648100] usb 6-2: new full-speed USB device number 3 using uhci_hcd
[    2.768112] usb 6-2: device descriptor read/64, error -71
[    2.992051] usb 6-2: device descriptor read/64, error -71
[    3.208047] usb 6-2: new full-speed USB device number 4 using uhci_hcd
[    3.273106] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.616044] usb 6-2: device not accepting address 4, error -71
[    3.728033] usb 6-2: new full-speed USB device number 5 using uhci_hcd
[    4.140073] usb 6-2: device not accepting address 5, error -71
[    4.140096] hub 6-0:1.0: unable to enumerate USB device on port 2

```

Output of lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 1058:071a Western Digital Technologies, Inc. My Passport 1TB

```

**Detailed output for the WD HDD**:
```

us 002 Device 003: ID 1058:071a Western Digital Technologies, Inc. My Passport 1TB
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1058 Western Digital Technologies, Inc.
  idProduct          0x071a My Passport 1TB
  bcdDevice           20.19
  iManufacturer           1 Western Digital
  iProduct                2 My Passport 071A
  iSerial                 3 575836314335304535363032
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
    MaxPower              500mA
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

```

From kern.log
```

Sep  7 12:53:16 zzz kernel: [78957.916335] usb 7-1: new full-speed USB device number 2 using uhci_hcd
Sep  7 12:53:16 zzz kernel: [78958.036341] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:16 zzz kernel: [78958.260336] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:16 zzz kernel: [78958.476270] usb 7-1: new full-speed USB device number 3 using uhci_hcd
Sep  7 12:53:16 zzz kernel: [78958.596340] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:16 zzz kernel: [78958.820293] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:17 zzz kernel: [78959.036349] usb 7-1: new full-speed USB device number 4 using uhci_hcd
Sep  7 12:53:17 zzz kernel: [78959.448066] usb 7-1: device not accepting address 4, error -71
Sep  7 12:53:17 zzz kernel: [78959.560291] usb 7-1: new full-speed USB device number 5 using uhci_hcd
Sep  7 12:53:18 zzz kernel: [78959.972302] usb 7-1: device not accepting address 5, error -71
Sep  7 12:53:18 zzz kernel: [78959.972348] hub 7-0:1.0: unable to enumerate USB device on port 1
Sep  7 12:53:24 zzz kernel: [78966.320318] usb 7-1: new full-speed USB device number 6 using uhci_hcd
Sep  7 12:53:24 zzz kernel: [78966.440169] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:24 zzz kernel: [78966.664294] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:25 zzz kernel: [78966.880044] usb 7-1: new full-speed USB device number 7 using uhci_hcd
Sep  7 12:53:25 zzz kernel: [78967.000109] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:25 zzz kernel: [78967.228030] usb 7-1: device descriptor read/64, error -71
Sep  7 12:53:25 zzz kernel: [78967.500025] usb 7-1: new full-speed USB device number 8 using uhci_hcd
Sep  7 12:53:26 zzz kernel: [78967.908126] usb 7-1: device not accepting address 8, error -71
Sep  7 12:53:26 zzz kernel: [78968.076067] usb 7-1: new full-speed USB device number 9 using uhci_hcd
Sep  7 12:53:26 zzz kernel: [78968.484057] usb 7-1: device not accepting address 9, error -71
Sep  7 12:53:26 zzz kernel: [78968.484081] hub 7-0:1.0: unable to enumerate USB device on port 1
Sep  7 12:54:44 zzz kernel: [79046.696156] usb 7-1: new full-speed USB device number 10 using uhci_hcd
Sep  7 12:54:44 zzz kernel: [79046.820067] usb 7-1: device descriptor read/64, error -71
Sep  7 12:54:45 zzz kernel: [79047.044082] usb 7-1: device descriptor read/64, error -71
Sep  7 12:54:45 zzz kernel: [79047.260076] usb 7-1: new full-speed USB device number 11 using uhci_hcd
Sep  7 12:54:45 zzz kernel: [79047.384100] usb 7-1: device descriptor read/64, error -71
Sep  7 12:54:45 zzz kernel: [79047.608139] usb 7-1: device descriptor read/64, error -71
Sep  7 12:54:45 zzz kernel: [79047.824087] usb 7-1: new full-speed USB device number 12 using uhci_hcd
Sep  7 12:54:46 zzz kernel: [79048.240104] usb 7-1: device not accepting address 12, error -71
Sep  7 12:54:46 zzz kernel: [79048.352074] usb 7-1: new full-speed USB device number 13 using uhci_hcd
Sep  7 12:54:46 zzz kernel: [79048.764184] usb 7-1: device not accepting address 13, error -71
Sep  7 12:54:46 zzz kernel: [79048.764229] hub 7-0:1.0: unable to enumerate USB device on port 1
Sep  7 12:55:34 zzz kernel: [79096.328076] usb 2-1: new high-speed USB device number 3 using ehci_hcd
Sep  7 12:55:34 zzz kernel: [79096.482331] Initializing USB Mass Storage driver...
Sep  7 12:55:34 zzz kernel: [79096.482458] scsi4 : usb-storage 2-1:1.0
Sep  7 12:55:34 zzz kernel: [79096.482524] usbcore: registered new interface driver usb-storage
Sep  7 12:55:34 zzz kernel: [79096.482526] USB Mass Storage support registered.
Sep  7 12:55:35 zzz kernel: [79097.482639] scsi 4:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
Sep  7 12:55:35 zzz kernel: [79097.484840] scsi 4:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
Sep  7 12:55:35 zzz kernel: [79097.486534] sd 4:0:0:0: Attached scsi generic sg1 type 0
Sep  7 12:55:35 zzz kernel: [79097.491811] sd 4:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  7 12:55:35 zzz kernel: [79097.492066] scsi 4:0:0:1: Attached scsi generic sg2 type 13
Sep  7 12:55:35 zzz kernel: [79097.493796] sd 4:0:0:0: [sdb] Write Protect is off
Sep  7 12:55:35 zzz kernel: [79097.493807] sd 4:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Sep  7 12:55:35 zzz kernel: [79097.495792] sd 4:0:0:0: [sdb] No Caching mode page found
Sep  7 12:55:35 zzz kernel: [79097.495801] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:55:35 zzz kernel: [79097.501325] sd 4:0:0:0: [sdb] No Caching mode page found
Sep  7 12:55:35 zzz kernel: [79097.501334] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:55:35 zzz kernel: [79097.530535]  sdb: sdb1 sdb2 sdb3 sdb4
Sep  7 12:55:35 zzz kernel: [79097.536266] sd 4:0:0:0: [sdb] No Caching mode page found
Sep  7 12:55:35 zzz kernel: [79097.536271] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:55:35 zzz kernel: [79097.536274] sd 4:0:0:0: [sdb] Attached SCSI disk
Sep  7 12:55:35 zzz kernel: [79097.568801] ses 4:0:0:1: Attached Enclosure device
Sep  7 12:56:46 zzz kernel: [79168.566998] usb 2-1: USB disconnect, device number 3
Sep  7 12:56:46 zzz kernel: [79168.820041] usb 2-1: new high-speed USB device number 4 using ehci_hcd
Sep  7 12:56:47 zzz kernel: [79168.964085] scsi5 : usb-storage 2-1:1.0
Sep  7 12:56:48 zzz kernel: [79169.966759] scsi 5:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
Sep  7 12:56:48 zzz kernel: [79169.968997] scsi 5:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
Sep  7 12:56:48 zzz kernel: [79169.970498] sd 5:0:0:0: Attached scsi generic sg1 type 0
Sep  7 12:56:48 zzz kernel: [79169.970793] ses 5:0:0:1: Attached Enclosure device
Sep  7 12:56:48 zzz kernel: [79169.971094] ses 5:0:0:1: Attached scsi generic sg2 type 13
Sep  7 12:56:48 zzz kernel: [79169.975155] sd 5:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  7 12:56:48 zzz kernel: [79169.977162] sd 5:0:0:0: [sdb] Write Protect is off
Sep  7 12:56:48 zzz kernel: [79169.977172] sd 5:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Sep  7 12:56:48 zzz kernel: [79169.980071] sd 5:0:0:0: [sdb] No Caching mode page found
Sep  7 12:56:48 zzz kernel: [79169.980081] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:56:48 zzz kernel: [79169.987802] sd 5:0:0:0: [sdb] No Caching mode page found
Sep  7 12:56:48 zzz kernel: [79169.987811] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:56:53 zzz kernel: [79175.304277]  sdb: sdb1 sdb2 sdb3 sdb4
Sep  7 12:56:53 zzz kernel: [79175.311995] sd 5:0:0:0: [sdb] No Caching mode page found
Sep  7 12:56:53 zzz kernel: [79175.312000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:56:53 zzz kernel: [79175.312016] sd 5:0:0:0: [sdb] Attached SCSI disk
Sep  7 12:56:57 zzz kernel: [79179.829835] usb 2-1: USB disconnect, device number 4
Sep  7 12:56:57 zzz kernel: [79179.836056] scsi 5:0:0:0: rejecting I/O to offline device
Sep  7 12:56:57 zzz kernel: [79179.836060] scsi 5:0:0:0: [sdb] killing request
Sep  7 12:56:57 zzz kernel: [79179.836079] scsi 5:0:0:0: [sdb] Unhandled error code
Sep  7 12:56:57 zzz kernel: [79179.836081] scsi 5:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep  7 12:56:57 zzz kernel: [79179.836085] scsi 5:0:0:0: [sdb] CDB: Read(10): 28 00 3d 09 34 f5 00 00 10 00
Sep  7 12:56:57 zzz kernel: [79179.836092] end_request: I/O error, dev sdb, sector 1024013557
Sep  7 12:56:57 zzz kernel: [79179.836096] Buffer I/O error on device sdb2, logical block 409607632
Sep  7 12:56:57 zzz kernel: [79179.836099] Buffer I/O error on device sdb2, logical block 409607633
Sep  7 12:56:57 zzz kernel: [79179.836101] Buffer I/O error on device sdb2, logical block 409607634
Sep  7 12:56:57 zzz kernel: [79179.836103] Buffer I/O error on device sdb2, logical block 409607635
Sep  7 12:56:57 zzz kernel: [79179.836105] Buffer I/O error on device sdb2, logical block 409607636
Sep  7 12:56:57 zzz kernel: [79179.836107] Buffer I/O error on device sdb2, logical block 409607637
Sep  7 12:56:57 zzz kernel: [79179.836109] Buffer I/O error on device sdb2, logical block 409607638
Sep  7 12:56:57 zzz kernel: [79179.836112] Buffer I/O error on device sdb2, logical block 409607639
Sep  7 12:56:57 zzz kernel: [79179.836116] Buffer I/O error on device sdb2, logical block 409607640
Sep  7 12:56:57 zzz kernel: [79179.836126] scsi 5:0:0:0: rejecting I/O to offline device
Sep  7 12:56:57 zzz kernel: [79179.836128] scsi 5:0:0:0: [sdb] killing request
Sep  7 12:56:57 zzz kernel: [79179.836166] scsi 5:0:0:0: [sdb] Unhandled error code
Sep  7 12:56:57 zzz kernel: [79179.836167] scsi 5:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep  7 12:56:57 zzz kernel: [79179.836170] scsi 5:0:0:0: [sdb] CDB: Read(10): 28 00 3d 09 35 05 00 00 f0 00
Sep  7 12:56:57 zzz kernel: [79179.836177] end_request: I/O error, dev sdb, sector 1024013573
Sep  7 12:56:58 zzz kernel: [79180.088062] usb 2-1: new high-speed USB device number 5 using ehci_hcd
Sep  7 12:56:59 zzz kernel: [79180.912081] scsi6 : usb-storage 2-1:1.0
Sep  7 12:57:00 zzz kernel: [79181.920130] scsi 6:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
Sep  7 12:57:00 zzz kernel: [79181.922288] scsi 6:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
Sep  7 12:57:00 zzz kernel: [79181.923841] sd 6:0:0:0: Attached scsi generic sg1 type 0
Sep  7 12:57:00 zzz kernel: [79181.924179] ses 6:0:0:1: Attached Enclosure device
Sep  7 12:57:00 zzz kernel: [79181.927129] sd 6:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  7 12:57:00 zzz kernel: [79181.927746] ses 6:0:0:1: Attached scsi generic sg2 type 13
Sep  7 12:57:00 zzz kernel: [79181.929130] sd 6:0:0:0: [sdb] Write Protect is off
Sep  7 12:57:00 zzz kernel: [79181.929140] sd 6:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Sep  7 12:57:00 zzz kernel: [79181.932333] sd 6:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:00 zzz kernel: [79181.932342] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:00 zzz kernel: [79181.941118] sd 6:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:00 zzz kernel: [79181.941123] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:00 zzz kernel: [79181.973401]  sdb: sdb1 sdb2 sdb3 sdb4
Sep  7 12:57:00 zzz kernel: [79181.982633] sd 6:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:00 zzz kernel: [79181.982638] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:00 zzz kernel: [79181.982642] sd 6:0:0:0: [sdb] Attached SCSI disk
Sep  7 12:57:20 zzz kernel: [79202.058994] usb 2-1: USB disconnect, device number 5
Sep  7 12:57:20 zzz kernel: [79202.312031] usb 2-1: new high-speed USB device number 6 using ehci_hcd
Sep  7 12:57:20 zzz kernel: [79202.446464] scsi7 : usb-storage 2-1:1.0
Sep  7 12:57:21 zzz kernel: [79203.446441] scsi 7:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
Sep  7 12:57:21 zzz kernel: [79203.448526] scsi 7:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
Sep  7 12:57:21 zzz kernel: [79203.449393] sd 7:0:0:0: Attached scsi generic sg1 type 0
Sep  7 12:57:21 zzz kernel: [79203.449464] ses 7:0:0:1: Attached Enclosure device
Sep  7 12:57:21 zzz kernel: [79203.449754] ses 7:0:0:1: Attached scsi generic sg2 type 13
Sep  7 12:57:21 zzz kernel: [79203.450138] sd 7:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  7 12:57:21 zzz kernel: [79203.454391] sd 7:0:0:0: [sdb] Write Protect is off
Sep  7 12:57:21 zzz kernel: [79203.454396] sd 7:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Sep  7 12:57:21 zzz kernel: [79203.457279] sd 7:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:21 zzz kernel: [79203.457284] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:21 zzz kernel: [79203.465790] sd 7:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:21 zzz kernel: [79203.465799] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:21 zzz kernel: [79203.497657]  sdb: sdb1 sdb2 sdb3 sdb4
Sep  7 12:57:21 zzz kernel: [79203.508651] sd 7:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:21 zzz kernel: [79203.508656] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:21 zzz kernel: [79203.508660] sd 7:0:0:0: [sdb] Attached SCSI disk
Sep  7 12:57:30 zzz kernel: [79212.120816] usb 2-1: USB disconnect, device number 6
Sep  7 12:57:30 zzz kernel: [79212.396054] usb 2-1: new high-speed USB device number 7 using ehci_hcd
Sep  7 12:57:30 zzz kernel: [79212.532397] scsi8 : usb-storage 2-1:1.0
Sep  7 12:57:31 zzz kernel: [79213.534494] scsi 8:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
Sep  7 12:57:31 zzz kernel: [79213.536601] scsi 8:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
Sep  7 12:57:31 zzz kernel: [79213.537357] sd 8:0:0:0: Attached scsi generic sg1 type 0
Sep  7 12:57:31 zzz kernel: [79213.537528] ses 8:0:0:1: Attached Enclosure device
Sep  7 12:57:31 zzz kernel: [79213.539767] ses 8:0:0:1: Attached scsi generic sg2 type 13
Sep  7 12:57:31 zzz kernel: [79213.540097] sd 8:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
Sep  7 12:57:31 zzz kernel: [79213.543082] sd 8:0:0:0: [sdb] Write Protect is off
Sep  7 12:57:31 zzz kernel: [79213.543088] sd 8:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Sep  7 12:57:31 zzz kernel: [79213.545949] sd 8:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:31 zzz kernel: [79213.545952] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:31 zzz kernel: [79213.554452] sd 8:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:31 zzz kernel: [79213.554457] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:31 zzz kernel: [79213.555843]  sdb: sdb1 sdb2 sdb3 sdb4
Sep  7 12:57:31 zzz kernel: [79213.566827] sd 8:0:0:0: [sdb] No Caching mode page found
Sep  7 12:57:31 zzz kernel: [79213.566832] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep  7 12:57:31 zzz kernel: [79213.566836] sd 8:0:0:0: [sdb] Attached SCSI disk
Sep  7 12:57:37 zzz kernel: [79219.247983] WARNING! power/level is deprecated; use power/control instead
Sep  7 12:57:37 zzz kernel: [79219.332029] usb 2-1: USB disconnect, device number 7
Sep  7 12:58:00 zzz kernel: [79242.640109] usb 7-1: new full-speed USB device number 14 using uhci_hcd
Sep  7 12:58:00 zzz kernel: [79242.764042] usb 7-1: device descriptor read/64, error -71
Sep  7 12:58:01 zzz kernel: [79242.988066] usb 7-1: device descriptor read/64, error -71
Sep  7 12:58:01 zzz kernel: [79243.204081] usb 7-1: new full-speed USB device number 15 using uhci_hcd
Sep  7 12:58:01 zzz kernel: [79243.328075] usb 7-1: device descriptor read/64, error -71
Sep  7 12:58:01 zzz kernel: [79243.552094] usb 7-1: device descriptor read/64, error -71
Sep  7 12:58:01 zzz kernel: [79243.768317] usb 7-1: new full-speed USB device number 16 using uhci_hcd
Sep  7 12:58:02 zzz kernel: [79244.184052] usb 7-1: device not accepting address 16, error -71
Sep  7 12:58:02 zzz kernel: [79244.296072] usb 7-1: new full-speed USB device number 17 using uhci_hcd
Sep  7 12:58:02 zzz kernel: [79244.708064] usb 7-1: device not accepting address 17, error -71
Sep  7 12:58:02 zzz kernel: [79244.708132] hub 7-0:1.0: unable to enumerate USB device on port 1
Sep  7 12:58:46 zzz kernel: [79288.772124] usb 7-2: new full-speed USB device number 18 using uhci_hcd
Sep  7 12:58:47 zzz kernel: [79288.892146] usb 7-2: device descriptor read/64, error -71
Sep  7 12:58:47 zzz kernel: [79289.116038] usb 7-2: device descriptor read/64, error -71
Sep  7 12:58:47 zzz kernel: [79289.332093] usb 7-2: new full-speed USB device number 19 using uhci_hcd
Sep  7 12:58:47 zzz kernel: [79289.452061] usb 7-2: device descriptor read/64, error -71
Sep  7 12:58:47 zzz kernel: [79289.676093] usb 7-2: device descriptor read/64, error -71
Sep  7 12:58:48 zzz kernel: [79289.892077] usb 7-2: new full-speed USB device number 20 using uhci_hcd
Sep  7 12:58:48 zzz kernel: [79290.308072] usb 7-2: device not accepting address 20, error -71
Sep  7 12:58:48 zzz kernel: [79290.420035] usb 7-2: new full-speed USB device number 21 using uhci_hcd
Sep  7 12:58:48 zzz kernel: [79290.832182] usb 7-2: device not accepting address 21, error -71
Sep  7 12:58:48 zzz kernel: [79290.832222] hub 7-0:1.0: unable to enumerate USB device on port 2
Sep  7 12:59:50 zzz kernel: [79351.984341] usb 6-2: new full-speed USB device number 2 using uhci_hcd
Sep  7 12:59:50 zzz kernel: [79352.104123] usb 6-2: device descriptor read/64, error -71
Sep  7 12:59:50 zzz kernel: [79352.328344] usb 6-2: device descriptor read/64, error -71
Sep  7 12:59:50 zzz kernel: [79352.544335] usb 6-2: new full-speed USB device number 3 using uhci_hcd
Sep  7 12:59:50 zzz kernel: [79352.664331] usb 6-2: device descriptor read/64, error -71
Sep  7 12:59:51 zzz kernel: [79352.888338] usb 6-2: device descriptor read/64, error -71
Sep  7 12:59:51 zzz kernel: [79353.104056] usb 6-2: new full-speed USB device number 4 using uhci_hcd
Sep  7 12:59:51 zzz kernel: [79353.516323] usb 6-2: device not accepting address 4, error -71
Sep  7 12:59:51 zzz kernel: [79353.628344] usb 6-2: new full-speed USB device number 5 using uhci_hcd
Sep  7 12:59:52 zzz kernel: [79354.040087] usb 6-2: device not accepting address 5, error -71
Sep  7 12:59:52 zzz kernel: [79354.040135] hub 6-0:1.0: unable to enumerate USB device on port 2
Sep  7 13:00:36 zzz kernel: [79397.928341] usb 6-1: new full-speed USB device number 6 using uhci_hcd
Sep  7 13:00:36 zzz kernel: [79398.048307] usb 6-1: device descriptor read/64, error -71
Sep  7 13:00:36 zzz kernel: [79398.272341] usb 6-1: device descriptor read/64, error -71
Sep  7 13:00:36 zzz kernel: [79398.488270] usb 6-1: new full-speed USB device number 7 using uhci_hcd
Sep  7 13:00:36 zzz kernel: [79398.608332] usb 6-1: device descriptor read/64, error -71
Sep  7 13:00:36 zzz kernel: [79398.832344] usb 6-1: device descriptor read/64, error -71
Sep  7 13:00:37 zzz kernel: [79399.048107] usb 6-1: new full-speed USB device number 8 using uhci_hcd
Sep  7 13:00:37 zzz kernel: [79399.456315] usb 6-1: device not accepting address 8, error -71
Sep  7 13:00:37 zzz kernel: [79399.568184] usb 6-1: new full-speed USB device number 9 using uhci_hcd
Sep  7 13:00:38 zzz kernel: [79399.976271] usb 6-1: device not accepting address 9, error -71
Sep  7 13:00:38 zzz kernel: [79399.976315] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:23 zzz kernel: [79564.900310] usb 6-2: new full-speed USB device number 10 using uhci_hcd
Sep  7 13:03:23 zzz kernel: [79565.020358] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:23 zzz kernel: [79565.300340] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:23 zzz kernel: [79565.516144] usb 6-2: new full-speed USB device number 11 using uhci_hcd
Sep  7 13:03:23 zzz kernel: [79565.636332] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:24 zzz kernel: [79565.860302] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:24 zzz kernel: [79566.020349] hub 6-0:1.0: unable to enumerate USB device on port 2
Sep  7 13:03:24 zzz kernel: [79566.480340] usb 6-2: new full-speed USB device number 13 using uhci_hcd
Sep  7 13:03:24 zzz kernel: [79566.600171] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:24 zzz kernel: [79566.824336] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:25 zzz kernel: [79567.040341] usb 6-2: new full-speed USB device number 14 using uhci_hcd
Sep  7 13:03:25 zzz kernel: [79567.160304] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:25 zzz kernel: [79567.440052] usb 6-2: device descriptor read/64, error -71
Sep  7 13:03:25 zzz kernel: [79567.656333] usb 6-2: new full-speed USB device number 15 using uhci_hcd
Sep  7 13:03:26 zzz kernel: [79568.068325] usb 6-2: device not accepting address 15, error -71
Sep  7 13:03:26 zzz kernel: [79568.180375] usb 6-2: new full-speed USB device number 16 using uhci_hcd
Sep  7 13:03:26 zzz kernel: [79568.592322] usb 6-2: device not accepting address 16, error -71
Sep  7 13:03:26 zzz kernel: [79568.592366] hub 6-0:1.0: unable to enumerate USB device on port 2
Sep  7 13:03:46 zzz kernel: [79588.108067] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:46 zzz kernel: [79588.588301] usb 6-1: new full-speed USB device number 18 using uhci_hcd
Sep  7 13:03:46 zzz kernel: [79588.708331] usb 6-1: device descriptor read/64, error -71
Sep  7 13:03:47 zzz kernel: [79588.876385] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:51 zzz kernel: [79592.992335] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Sep  7 13:03:51 zzz kernel: [79593.248377] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:51 zzz kernel: [79593.760334] usb 6-1: new full-speed USB device number 20 using uhci_hcd
Sep  7 13:03:52 zzz kernel: [79593.880337] usb 6-1: device descriptor read/64, error -71
Sep  7 13:03:52 zzz kernel: [79594.048395] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:52 zzz kernel: [79594.472301] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:53 zzz kernel: [79595.000330] usb 6-1: new full-speed USB device number 22 using uhci_hcd
Sep  7 13:03:53 zzz kernel: [79595.120048] usb 6-1: device descriptor read/64, error -71
Sep  7 13:03:53 zzz kernel: [79595.288363] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:53 zzz kernel: [79595.528337] usb 6-1: new full-speed USB device number 23 using uhci_hcd
Sep  7 13:03:53 zzz kernel: [79595.648332] usb 6-1: device descriptor read/64, error -71
Sep  7 13:03:53 zzz kernel: [79595.816346] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:54 zzz kernel: [79596.432074] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:55 zzz kernel: [79596.928389] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:55 zzz kernel: [79597.424123] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:56 zzz kernel: [79597.920362] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:56 zzz kernel: [79598.416333] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:57 zzz kernel: [79598.912390] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:57 zzz kernel: [79599.408239] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:58 zzz kernel: [79599.904118] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:58 zzz kernel: [79600.400115] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:59 zzz kernel: [79600.896383] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:03:59 zzz kernel: [79601.392382] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:00 zzz kernel: [79601.888341] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:00 zzz kernel: [79602.384336] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:01 zzz kernel: [79602.880359] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:01 zzz kernel: [79603.376376] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:02 zzz kernel: [79603.872331] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:02 zzz kernel: [79604.368107] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:03 zzz kernel: [79604.864389] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:03 zzz kernel: [79605.360457] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:04 zzz kernel: [79605.856415] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:08 zzz kernel: [79609.972339] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Sep  7 13:04:08 zzz kernel: [79610.228378] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:08 zzz kernel: [79610.816382] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:13 zzz kernel: [79614.932335] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Sep  7 13:04:13 zzz kernel: [79615.188240] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:13 zzz kernel: [79615.776387] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:14 zzz kernel: [79616.272352] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:14 zzz kernel: [79616.768279] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:15 zzz kernel: [79617.264377] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:15 zzz kernel: [79617.760201] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:16 zzz kernel: [79618.008379] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:16 zzz kernel: [79618.504383] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:20 zzz kernel: [79622.620343] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Sep  7 13:04:21 zzz kernel: [79622.932343] usb 6-1: new full-speed USB device number 54 using uhci_hcd
Sep  7 13:04:21 zzz kernel: [79623.052339] usb 6-1: device descriptor read/64, error -71
Sep  7 13:04:21 zzz kernel: [79623.220319] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:21 zzz kernel: [79623.464448] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:22 zzz kernel: [79623.960379] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:22 zzz kernel: [79624.456082] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:23 zzz kernel: [79624.952338] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:23 zzz kernel: [79625.448080] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:24 zzz kernel: [79625.944379] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:24 zzz kernel: [79626.192192] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:24 zzz kernel: [79626.688180] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:25 zzz kernel: [79627.184257] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:25 zzz kernel: [79627.680285] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:26 zzz kernel: [79628.176380] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:26 zzz kernel: [79628.672384] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:27 zzz kernel: [79629.168115] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:27 zzz kernel: [79629.664333] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:28 zzz kernel: [79630.160188] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:28 zzz kernel: [79630.656336] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:29 zzz kernel: [79631.152302] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:29 zzz kernel: [79631.648391] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:30 zzz kernel: [79632.144107] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:30 zzz kernel: [79632.640384] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:31 zzz kernel: [79633.136312] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:31 zzz kernel: [79633.632384] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:32 zzz kernel: [79634.128064] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:32 zzz kernel: [79634.624377] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:33 zzz kernel: [79635.120281] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:33 zzz kernel: [79635.616364] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:34 zzz kernel: [79636.112076] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:34 zzz kernel: [79636.608351] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:35 zzz kernel: [79637.104099] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:35 zzz kernel: [79637.600174] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:36 zzz kernel: [79638.096348] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:36 zzz kernel: [79638.592424] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:37 zzz kernel: [79639.088337] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:37 zzz kernel: [79639.584378] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:04:49 zzz kernel: [79651.196344] usb 7-1: new full-speed USB device number 22 using uhci_hcd
Sep  7 13:04:49 zzz kernel: [79651.316293] usb 7-1: device descriptor read/64, error -71
Sep  7 13:04:49 zzz kernel: [79651.540331] usb 7-1: device descriptor read/64, error -71
Sep  7 13:04:49 zzz kernel: [79651.756286] usb 7-1: new full-speed USB device number 23 using uhci_hcd
Sep  7 13:04:50 zzz kernel: [79651.876286] usb 7-1: device descriptor read/64, error -71
Sep  7 13:04:50 zzz kernel: [79652.100125] usb 7-1: device descriptor read/64, error -71
Sep  7 13:04:50 zzz kernel: [79652.316344] usb 7-1: new full-speed USB device number 24 using uhci_hcd
Sep  7 13:04:50 zzz kernel: [79652.728281] usb 7-1: device not accepting address 24, error -71
Sep  7 13:04:50 zzz kernel: [79652.840344] usb 7-1: new full-speed USB device number 25 using uhci_hcd
Sep  7 13:04:51 zzz kernel: [79653.256325] usb 7-1: device not accepting address 25, error -71
Sep  7 13:04:51 zzz kernel: [79653.256368] hub 7-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:05:30 zzz kernel: [79692.840339] usb 6-1: new full-speed USB device number 89 using uhci_hcd
Sep  7 13:05:31 zzz kernel: [79692.960335] usb 6-1: device descriptor read/64, error -71
Sep  7 13:05:31 zzz kernel: [79693.184127] usb 6-1: device descriptor read/64, error -71
Sep  7 13:05:31 zzz kernel: [79693.400126] usb 6-1: new full-speed USB device number 90 using uhci_hcd
Sep  7 13:05:31 zzz kernel: [79693.520280] usb 6-1: device descriptor read/64, error -71
Sep  7 13:05:31 zzz kernel: [79693.744334] usb 6-1: device descriptor read/64, error -71
Sep  7 13:05:32 zzz kernel: [79693.960366] usb 6-1: new full-speed USB device number 91 using uhci_hcd
Sep  7 13:05:32 zzz kernel: [79694.376060] usb 6-1: device not accepting address 91, error -71
Sep  7 13:05:32 zzz kernel: [79694.488343] usb 6-1: new full-speed USB device number 92 using uhci_hcd
Sep  7 13:05:33 zzz kernel: [79694.904320] usb 6-1: device not accepting address 92, error -71
Sep  7 13:05:33 zzz kernel: [79694.904362] hub 6-0:1.0: unable to enumerate USB device on port 1
Sep  7 13:06:28 zzz kernel: [79750.036368] usb 6-2: new full-speed USB device number 93 using uhci_hcd
Sep  7 13:06:28 zzz kernel: [79750.156254] usb 6-2: device descriptor read/64, error -71
Sep  7 13:06:28 zzz kernel: [79750.380069] usb 6-2: device descriptor read/64, error -71
Sep  7 13:06:28 zzz kernel: [79750.652333] usb 6-2: new full-speed USB device number 94 using uhci_hcd
Sep  7 13:06:28 zzz kernel: [79750.772333] usb 6-2: device descriptor read/64, error -71
Sep  7 13:06:29 zzz kernel: [79750.996268] usb 6-2: device descriptor read/64, error -71
Sep  7 13:06:29 zzz kernel: [79751.212274] usb 6-2: new full-speed USB device number 95 using uhci_hcd
Sep  7 13:06:29 zzz kernel: [79751.620321] usb 6-2: device not accepting address 95, error -71
Sep  7 13:06:29 zzz kernel: [79751.788335] usb 6-2: new full-speed USB device number 96 using uhci_hcd
Sep  7 13:06:30 zzz kernel: [79752.200143] usb 6-2: device not accepting address 96, error -71
Sep  7 13:06:30 zzz kernel: [79752.200184] hub 6-0:1.0: unable to enumerate USB device on port 2
Sep  7 13:08:40 zzz kernel: [79882.730002] init: tty4 main process (1197) killed by TERM signal

```


Other details that might be useful:

Linux version 3.2.0-64-generic (buildd@kissel)

Have rebooted the system multiple times but no help. Checked the drive SMART status on the other machine and all showed good. Tried with a different cable and did not work on Linux.
I also tried it on another desktop that has Mint OS running and same error messages.

As I was able to use the drive on another Windows box, I let it run there and backed up some data. After 4-5 hours of it running without any issues in Windows, I plugged it back in my laptop (Kubuntu) and it mounted succesfully with these in the dmesg logs. Removed it properly and tried then on the desktop with Mint and worked there also smoothly.
```

[23954.020081] usb 2-1: reset high-speed USB device number 3 using ehci_hcd
[23954.153250] scsi5 : usb-storage 2-1:1.0
[23955.154661] scsi 5:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
[23955.156659] scsi 5:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
[23955.157442] sd 5:0:0:0: Attached scsi generic sg1 type 0
[23955.157581] ses 5:0:0:1: Attached Enclosure device
[23955.160160] sd 5:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
[23955.161366] ses 5:0:0:1: Attached scsi generic sg2 type 13
[23955.162260] sd 5:0:0:0: [sdb] Write Protect is off
[23955.162264] sd 5:0:0:0: [sdb] Mode Sense: 2b 00 10 08
[23955.165282] sd 5:0:0:0: [sdb] No Caching mode page found
[23955.165287] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[23955.173788] sd 5:0:0:0: [sdb] No Caching mode page found
[23955.173793] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[23955.213664]  sdb: sdb1 sdb2 sdb3 sdb4
[23955.225031] sd 5:0:0:0: [sdb] No Caching mode page found
[23955.225035] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[23955.225038] sd 5:0:0:0: [sdb] Attached SCSI disk
[23988.837261] **WARNING! power/level is deprecated; use power/control instead**
[23988.916075] usb 2-1: USB disconnect, device number 3

```

Somewhere it was mentioned that it could be due to some kernel bug. Not able to figure out what exactly the problem was. Any help will be greatly appreciated.

---

### Post by KumarAseem on 2014-09-07
I had it plugged into the Mint box. After sometime I plugged it out and plugged it into my laptop and again the same errors. Tried another port and same error. Tried another port and it got attached. Really no pattern to it and is driving me crazy. I am worried about data loss as yet to back up all the data. Ordered a new drive for backing up the data and it will arrive in 2-3 days only.
```

[26468.456114] usb 6-2: new full-speed USB device number 6 using uhci_hcd
[26468.580068] usb 6-2: device descriptor read/64, error -71
[26468.860054] usb 6-2: device descriptor read/64, error -71
[26469.076078] usb 6-2: new full-speed USB device number 7 using uhci_hcd
[26469.200089] usb 6-2: device descriptor read/64, error -71
[26469.480075] usb 6-2: device descriptor read/64, error -71
[26469.696037] usb 6-2: new full-speed USB device number 8 using uhci_hcd
[26470.104065] usb 6-2: device not accepting address 8, error -71
[26470.216104] usb 6-2: new full-speed USB device number 9 using uhci_hcd
[26470.628059] usb 6-2: device not accepting address 9, error -71
[26470.628103] hub 6-0:1.0: unable to enumerate USB device on port 2
[26495.076047] usb 6-1: new full-speed USB device number 10 using uhci_hcd
[26495.196050] usb 6-1: device descriptor read/64, error -71
[26495.476076] usb 6-1: device descriptor read/64, error -71
[26495.692073] usb 6-1: new full-speed USB device number 11 using uhci_hcd
[26495.816073] usb 6-1: device descriptor read/64, error -71
[26496.040077] usb 6-1: device descriptor read/64, error -71
[26496.256056] usb 6-1: new full-speed USB device number 12 using uhci_hcd
[26496.664054] usb 6-1: device not accepting address 12, error -71
[26496.776114] usb 6-1: new full-speed USB device number 13 using uhci_hcd
[26497.188041] usb 6-1: device not accepting address 13, error -71
[26497.188069] hub 6-0:1.0: unable to enumerate USB device on port 1
[26526.824049] usb 6-1: new full-speed USB device number 14 using uhci_hcd
[26526.948045] usb 6-1: device descriptor read/64, error -71
[26527.176032] usb 6-1: device descriptor read/64, error -71
[26527.392064] usb 6-1: new full-speed USB device number 15 using uhci_hcd
[26527.516072] usb 6-1: device descriptor read/64, error -71
[26527.740072] usb 6-1: device descriptor read/64, error -71
[26528.012062] usb 6-1: new full-speed USB device number 16 using uhci_hcd
[26528.420080] usb 6-1: device not accepting address 16, error -71
[26528.588109] usb 6-1: new full-speed USB device number 17 using uhci_hcd
[26529.000050] usb 6-1: device not accepting address 17, error -71
[26529.000075] hub 6-0:1.0: unable to enumerate USB device on port 1
[26563.292086] usb 2-3: new high-speed USB device number 6 using ehci_hcd
[26563.425800] scsi6 : usb-storage 2-3:1.0
[26564.426640] scsi 6:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
[26564.428997] scsi 6:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
[26564.430684] sd 6:0:0:0: Attached scsi generic sg1 type 0
[26564.431020] ses 6:0:0:1: Attached Enclosure device
[26564.431297] ses 6:0:0:1: Attached scsi generic sg2 type 13
[26564.436544] sd 6:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
[26564.438848] sd 6:0:0:0: [sdb] Write Protect is off
[26564.438859] sd 6:0:0:0: [sdb] Mode Sense: 2b 00 10 08
[26564.441725] sd 6:0:0:0: [sdb] No Caching mode page found
[26564.441734] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26564.449328] sd 6:0:0:0: [sdb] No Caching mode page found
[26564.449330] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26564.482135]  sdb: sdb1 sdb2 sdb3 sdb4
[26564.493218] sd 6:0:0:0: [sdb] No Caching mode page found
[26564.493223] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[26564.493227] sd 6:0:0:0: [sdb] Attached SCSI disk
[27445.946438] usb 2-3: USB disconnect, device number 6
[27446.216047] usb 2-3: new high-speed USB device number 7 using ehci_hcd
[27446.350135] scsi7 : usb-storage 2-3:1.0
[27447.350393] scsi 7:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
[27447.352491] scsi 7:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
[27447.354606] sd 7:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
[27447.354790] sd 7:0:0:0: Attached scsi generic sg1 type 0
[27447.355824] ses 7:0:0:1: Attached Enclosure device
[27447.355898] ses 7:0:0:1: Attached scsi generic sg2 type 13
[27447.356616] sd 7:0:0:0: [sdb] Write Protect is off
[27447.356619] sd 7:0:0:0: [sdb] Mode Sense: 2b 00 10 08
[27447.359608] sd 7:0:0:0: [sdb] No Caching mode page found
[27447.359611] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[27447.366246] sd 7:0:0:0: [sdb] No Caching mode page found
[27447.366250] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[27451.440687] usb 2-3: USB disconnect, device number 7
[27451.443074] ses 7:0:0:1: Failed to get diagnostic page 0x10000
[27451.443080] ses 7:0:0:1: Failed to bind enclosure -19
[27451.448047] sd 7:0:0:0: [sdb] Unhandled error code
[27451.448050] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[27451.448054] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[27451.448061] end_request: I/O error, dev sdb, sector 0
[27451.448064] quiet_error: 21 callbacks suppressed
[27451.448066] Buffer I/O error on device sdb, logical block 0
[27451.448130] ldm_validate_partition_table(): Disk read failed.
[27451.448153] Dev sdb: unable to read RDB block 0
[27451.448186]  sdb: unable to read partition table
[27451.448311] sd 7:0:0:0: [sdb] READ CAPACITY failed
[27451.448313] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[27451.448316] sd 7:0:0:0: [sdb] Sense not available.
[27451.448334] sd 7:0:0:0: [sdb] No Caching mode page found
[27451.448337] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[27451.448339] sd 7:0:0:0: [sdb] Attached SCSI disk
[27451.688064] usb 2-3: new high-speed USB device number 8 using ehci_hcd
[27453.600823] scsi8 : usb-storage 2-3:1.0
[27454.613587] scsi 8:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
[27454.616930] scsi 8:0:0:1: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
[27454.618267] sd 8:0:0:0: Attached scsi generic sg1 type 0
[27454.618343] ses 8:0:0:1: Attached Enclosure device
[27454.619636] ses 8:0:0:1: Attached scsi generic sg2 type 13
[27454.619691] sd 8:0:0:0: [sdb] 1953468416 512-byte logical blocks: (1.00 TB/931 GiB)
[27454.624038] sd 8:0:0:0: [sdb] Write Protect is off
[27454.624043] sd 8:0:0:0: [sdb] Mode Sense: 2b 00 10 08
[27454.627873] sd 8:0:0:0: [sdb] No Caching mode page found
[27454.627876] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[27454.636451] sd 8:0:0:0: [sdb] No Caching mode page found
[27454.636455] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[27454.669848]  sdb: sdb1 sdb2 sdb3 sdb4
[27454.680829] sd 8:0:0:0: [sdb] No Caching mode page found
[27454.680833] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[27454.680836] sd 8:0:0:0: [sdb] Attached SCSI disk

```

---

### Post by Vladlenin5000 on 2014-09-07
Please post the results in CODE (Go Advance, click # and paste inside). It's not practical to scroll down so much...

A question before anything else: What version of Kubuntu are you running? The [COLOR=#000000]3.2.0-64-generic kernel is very old...[/COLOR]

---

### Post by KumarAseem on 2014-09-07
I am running the 12.04LTS version of Kubuntu (Precise Pangolin), 64bit image.

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

I am not sure if the older kernel version could be a factor here as the drive used to work and sometimes does work on this machine.

---

### Post by KumarAseem on 2014-09-12
Bump!

---

