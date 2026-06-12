---
title: "USB key not detected properly by Ubuntu"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by unclejames on 2008-01-13
I have two Ubuntu machines in the house: a Sony Vaio can see my Lexar USB key (and others) quite perfectly; however this HP Compaq tc4200 has problems.

Plugging in any USB stick shows a few flashing blue lights on the stick itself, and it appears in Places > Computer, but not on my desktop.

An attempt to right-click the drive in Places > Computer, and mount the drive, results in nothing: no flashing light on the drive, and nothing happening on the computer itself.

Using the Lexar, since I know it works fine on Ubuntu on the Sony, this is the output of lsusb
```
james@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05dc:a560 Lexar Media, Inc. 
Bus 001 Device 001: ID 0000:0000  

```


This is the output of lsusb -v for this particular drive...

```
Bus 001 Device 003: ID 05dc:a560 Lexar Media, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0xa560 
  bcdDevice           30.00
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
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

Plugging the device in gives me, in kern.log:
```
Jan 13 22:55:54 ubuntu kernel: [44666.824000] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb 1-3: configuration #1 chosen from 1 choice
Jan 13 22:55:54 ubuntu kernel: [44666.956000] scsi3 : SCSI emulation for USB Mass Storage devices
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb-storage: device found at 4
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb-storage: waiting for device to settle before scanning
Jan 13 22:55:59 ubuntu kernel: [44671.956000] usb-storage: device scan complete
Jan 13 22:55:59 ubuntu kernel: [44671.956000] scsi 3:0:0:0: Direct-Access     LEXAR    JD FIREFLY       3000 PQ: 0 ANSI: 0 CCS
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] 7928832 512-byte hardware sectors (4060 MB)
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Write Protect is off
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] 7928832 512-byte hardware sectors (4060 MB)
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Write Protect is off
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan 13 22:55:59 ubuntu kernel: [44671.976000]  sdb: sdb1
Jan 13 22:55:59 ubuntu kernel: [44672.132000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jan 13 22:55:59 ubuntu kernel: [44672.132000] sd 3:0:0:0: Attached scsi generic sg1 type 0
```

...in messages...
> Jan 13 22:55:54 ubuntu kernel: [44666.824000] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb 1-3: configuration #1 chosen from 1 choice
Jan 13 22:55:54 ubuntu kernel: [44666.956000] scsi3 : SCSI emulation for USB Mass Storage devices
Jan 13 22:55:59 ubuntu kernel: [44671.956000] scsi 3:0:0:0: Direct-Access     LEXAR    JD FIREFLY       3000 PQ: 0 ANSI: 0 CCS
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] 7928832 512-byte hardware sectors (4060 MB)
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Write Protect is off
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] 7928832 512-byte hardware sectors (4060 MB)
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Write Protect is off
Jan 13 22:55:59 ubuntu kernel: [44671.976000]  sdb: sdb1
Jan 13 22:55:59 ubuntu kernel: [44672.132000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jan 13 22:55:59 ubuntu kernel: [44672.132000] sd 3:0:0:0: Attached scsi generic sg1 type 0

...in syslog:
```
Jan 13 22:55:54 ubuntu kernel: [44666.824000] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb 1-3: configuration #1 chosen from 1 choice
Jan 13 22:55:54 ubuntu kernel: [44666.956000] scsi3 : SCSI emulation for USB Mass Storage devices
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb-storage: device found at 4
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb-storage: waiting for device to settle before scanning
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.344922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106'). 
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.401171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0'). 
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.405930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_usbraw'). 
Jan 13 22:55:59 ubuntu kernel: [44671.956000] usb-storage: device scan complete
Jan 13 22:55:59 ubuntu kernel: [44671.956000] scsi 3:0:0:0: Direct-Access     LEXAR    JD FIREFLY       3000 PQ: 0 ANSI: 0 CCS
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] 7928832 512-byte hardware sectors (4060 MB)
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Write Protect is off
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] 7928832 512-byte hardware sectors (4060 MB)
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Write Protect is off
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Jan 13 22:55:59 ubuntu kernel: [44671.976000]  sdb: sdb1
Jan 13 22:55:59 ubuntu kernel: [44672.132000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.557526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.560153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host_scsi_device_lun0'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.582475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 13 22:55:59 ubuntu kernel: [44672.132000] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.769442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_LEXAR_JD_FIREFLY_0A4F1006211843151106_0_0'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.925853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_70AC_CD3B'). 
```

...in debug:
```
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb-storage: device found at 4
Jan 13 22:55:54 ubuntu kernel: [44666.956000] usb-storage: waiting for device to settle before scanning
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.344922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106'). 
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.401171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0'). 
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.405930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_usbraw'). 
Jan 13 22:55:59 ubuntu kernel: [44671.956000] usb-storage: device scan complete
Jan 13 22:55:59 ubuntu kernel: [44671.972000] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 13 22:55:59 ubuntu kernel: [44671.976000] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.557526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.560153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host_scsi_device_lun0'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.582475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.769442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_LEXAR_JD_FIREFLY_0A4F1006211843151106_0_0'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.925853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_70AC_CD3B'). 
```

...in daemon.log:
```
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.344922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106'). 
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.401171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0'). 
Jan 13 22:55:54 ubuntu NetworkManager: <debug> [1200264954.405930] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_usbraw'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.557526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.560153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host_scsi_device_lun0'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.582475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a560_0A4F1006211843151106_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.769442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_LEXAR_JD_FIREFLY_0A4F1006211843151106_0_0'). 
Jan 13 22:55:59 ubuntu NetworkManager: <debug> [1200264959.925853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_70AC_CD3B'). 
```

Hope all this helps someone help me get USB keys working on this Ubuntu box: I love Ubuntu otherwise!

---

