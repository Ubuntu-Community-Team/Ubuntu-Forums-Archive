---
title: "Cannot mount Samsung D900 phone"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by ajvdvegt on 2007-02-04
I can't mount my Samsung D900 phone. If I insert the USB cable and set thephone to 'mass storage' mode, I get these lines in /var/log/messages:

```
Feb  4 14:56:55 localhost kernel: [17184436.748000] usb 3-2: new full speed USB device using ohci_hcd and address 9
Feb  4 14:56:56 localhost kernel: [17184436.972000] usb 3-2: configuration #3 chosen from 1 choice
Feb  4 14:56:56 localhost kernel: [17184436.976000] scsi8 : SCSI emulation for USB Mass Storage devices
Feb  4 14:57:01 localhost kernel: [17184441.984000]   Vendor:           Model:                   Rev:     
Feb  4 14:57:01 localhost kernel: [17184441.984000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb  4 14:57:01 localhost kernel: [17184442.016000] sd 8:0:0:0: Attached scsi removable disk sda
Feb  4 14:57:01 localhost kernel: [17184442.016000] sd 8:0:0:0: Attached scsi generic sg0 type 0
```
It's not automounted, and when I try to mount /dev/sda manually (mount /dev/sda /media/usbdisk1 -t vfat) it returns 'mount: No medium found'.

`lshal` returns this:```
udi = '/org/freedesktop/Hal/devices/storage_serial_Samsung_SAMSUNG_Mobile_USB_Modem_354299_01_874555'
  info.addons = {'hald-addon-storage'} (string list)
  storage.policy.should_mount = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Samsung_SAMSUNG_Mobile_USB_Modem_354299_01_874555'  (st
ring)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_Samsung_SAMSUNG_Mobile_USB_Modem_354299_01_874555'  (string)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = true  (bool)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.product = ''  (string)
  info.vendor = ''  (string)
  storage.removable = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/usb_device_4e8_665c_354299_01_874555_if0'  (string)
  storage.lun = 0  (0x0)  (int)
  storage.firmware_version = '0100'  (string)
  storage.serial = 'Samsung_SAMSUNG_Mobile_USB_Modem_354299-01-874555'  (string)
  storage.vendor = ''  (string)
  storage.model = ''  (string)
  storage.drive_type = 'disk'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = false  (bool)
  storage.bus = 'usb'  (string)
  block.is_volume = false  (bool)
  block.minor = 0  (0x0)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_4e8_665c_354299_01_874555_if0_scsi_host_scsi_device_lun0'  (string)
  linux.sysfs_path_device = '/sys/block/sda'  (string)
  linux.sysfs_path = '/sys/block/sda'  (string)

```

And lsusb returns this:
```
Bus 003 Device 009: ID 04e8:665c Samsung Electronics Co., Ltd 
```

I tried formatting it as well, but mkfs also returns 'no medium found'. Any ideas what might be wrong? Seems like a usb-storage bug to me.....

---

### Post by ajvdvegt on 2007-02-08
Despite the enormous amount of reactions in this thread, I'd figured it might be useful to post a little more info: It seems you can mount an SD card if you insert it, but I don't have one of those (yet)...

---

### Post by Choad on 2007-03-14
i spent ages trying to figure this out. turns out the "usb mode" of the d900 means the d900 acts as a card reader for whatever memory card you have in the phone (ie none by default)

you have to transfer files by bluetooth, or by windows using their shitty software.

---

### Post by crosslink on 2008-06-15
Just a bit more detail...

With regard to phone book sync, Choad is right. (Pretty big deal for me, and quite disappointing.)

With regard to moving other files (pictures, mp3 files) between computer and the phone's (optional) card, USB mass storage works fine on my Gutsy machine, no extra configuration needed.

Details:
* USB connector
* using 2gb card in phone (micro SD, brand: PNY)
* On phone: Settings > phone settings > USB Settings > Mass Storage

---

