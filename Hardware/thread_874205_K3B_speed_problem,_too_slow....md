---
title: "K3B speed problem, too slow..."
date: 2008-07-29
forum: Hardware
---

### Post by Ashrael on 2008-07-29
K3B always burned my cd's slower, but now it's getting very slow, since I installed 8.04.1 I cannot burn faster than 5645 KB/s????


output from K3B started from terminal:
```

k3b
kbuildsycoca running...
adaptr@Fairyworld:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD_RW_ND_3500AG to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 0, id: 1, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 5645
DiskInfo:
Mediatype:       CD-R
Current Profile: CD-R
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        79:57:74 (LBA 359849) (736970752 Bytes)
Remaining size:  79:57:74 (LBA 359849) (736970752 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 4
(K3bDevice::Device) /dev/scd0 : 5645 KB/s
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1411 KB/s
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         _NEC
Description:    DVD_RW ND-3500AG
Version:        2.98
Write speed:    5645
Profiles:       DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
(K3bDevice::DeviceManager) request for empty device!
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_DVD_RW_ND_3500AG
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_DVD_RW_ND_3500AG
removing udi /org/freedesktop/Hal/devices/volume_empty_cd_r
Launched ok, pid = 6276
ICE default IO error handler doing an exit(), pid = 6273, errno = 11

```

ANYONE got a clue? libata??? it used to work perfectly with the same cable & board...

TIA!

---

