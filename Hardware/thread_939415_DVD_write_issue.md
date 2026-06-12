---
title: "DVD write issue"
date: 2008-10-05
forum: Hardware
---

### Post by ARhere on 2008-10-05
This is not a dupe, but a seporate issues then [this thread]("http://ubuntuforums.org/showthread.php?p=5914495#post5914495"), but I am certain they are related.  REason is, I was able to burn 8x DVD+R's fine, but now they are not available.  16x DVD+R's gives me the following issues!

I cannot seem to burn a DVD, but a CD burns just fine.  Whne I place a blank 16x DVD disk into my drive, Ubuntu reconizes it as a blank disk and askes me if I wish to create a new disk.  (*so far, so great*) when I hit the "BURN" button after selecting files, it just says...
[quote=COMPUTER]There was an error writing to the disc:
Unhandled error, aborting[/quote]

***EDIT: dmesg had nothing to do with the burn process.***

Everthing looks ok with mediainfo...
```
andrew@GamePC:~$ sudo dvd+rw-mediainfo /dev/dvd2
[sudo] password for andrew: 
INQUIRY:                [LITE-ON ][DVDRW SOHW-1673S][JS02]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Media ID:              CMC MAG/M01
 Current Write Speed:   16.0x1385=22160KB/s
 Write Speed #0:        16.0x1385=22160KB/s
 Write Speed #1:        12.0x1385=16620KB/s
 Write Speed #2:        8.0x1385=11080KB/s
 Write Speed #3:        6.0x1385=8310KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     6.4x1385=8864KB/s@[0 -> 0]
 Speed Descriptor#0:    00/0 R@3.2x1385=4432KB/s W@16.0x1385=22160KB/s
 Speed Descriptor#1:    00/0 R@3.2x1385=4432KB/s W@12.0x1385=16620KB/s
 Speed Descriptor#2:    00/0 R@3.2x1385=4432KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#3:    00/0 R@3.2x1385=4432KB/s W@6.0x1385=8310KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           2295104*2KB
 Track Size:            2295104*2KB
 ROM Compatibility LBA: 262144
READ CAPACITY:          0*2048=0
```

My DVD ROM drive is a LITE-ON DVD drive on a USB to IDE adapter.  Below is the **lsusb** and the LONG code block is a dump of my **lshal**
```
andrew@GamePC:~$ lsusb 
Bus 004 Device 027: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
...
udi = '/org/freedesktop/Hal/devices/storage_serial_LITE_ON_DVDRW_SOHW_1673S_222222222222_0_0'
  access_control.file = '/dev/scd0'  (string)
  access_control.type = 'cdrom'  (string)
  block.device = '/dev/scd0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_LITE_ON_DVDRW_SOHW_1673S_222222222222_0_0'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom', 'access_control'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_152d_2338_222222222222_if0_scsi_host_scsi_device_lun0'  (string)
  info.product = 'DVDRW SOHW-1673S'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_LITE_ON_DVDRW_SOHW_1673S_222222222222_0_0'  (string)
  info.vendor = 'LITE-ON'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'usb'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 8467  (0x2113)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8467  (0x2113)  (int)
  storage.cdrom.write_speeds = {'8467', '7056', '5645', '4234', '2822', '2112', '1764', '1411', '706'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'JS02'  (string)
  storage.hotpluggable = true  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'DVDRW SOHW-1673S'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/usb_device_152d_2338_222222222222_if0'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.serial = 'LITE-ON_DVDRW_SOHW-1673S_222222222222-0:0'  (string)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'LITE-ON'  (string)
```

I am stumped... any ideas?

-AR

---

