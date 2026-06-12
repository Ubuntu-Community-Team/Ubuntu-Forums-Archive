---
title: "Nor brasero nor K3B recognize my DVD-RW drive."
date: 2008-11-19
forum: Hardware
---

### Post by Copitox on 2008-11-19
Hi! as the title says, nor brasero nor K3B recognise my DVD-RW drive, but the strange thing is that the system does, if i put a cd or a dvd my laptop reads it.. but this burning programs doesn't, in fact it don't even let me select the drive. THE STRANGEST thing is that it works if i run the program in as root!

This is what the console spits when i run it as normal user and root.


Normal User:

```
copitox@copitox-laptop:~$ k3b
kbuildsycoca running...
copitox@copitox-laptop:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD__RW_GSA_T21N to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
(K3bDevice::Device) could not open device /dev/scd0 for reading
                    (Permiso denegado)
could not open device /dev/scd0 (Permiso denegado)
/dev/scd0 resolved to /dev/scd0
(K3bDevice::Device) could not open device /dev/scd0 for reading
                    (Permiso denegado)
could not open device /dev/scd0 (Permiso denegado)
Devices:
------------------------------
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available

```

Root:

```
copitox@copitox-laptop:~$ sudo k3b
copitox@copitox-laptop:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD__RW_GSA_T21N to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 4, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 706
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: HL-DT-ST DVD+-RW GSA-T21N
DiskInfo:
Mediatype:       CD-RW
Current Profile: CD-RW
Disk state:      empty
Empty:           1
Rewritable:      1
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        79:57:74 (LBA 359849) (736970752 Bytes)
Remaining size:  79:57:74 (LBA 359849) (736970752 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 1
(K3bDevice::Device) /dev/scd0 : 706 KB/s
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         HL-DT-ST
Description:    DVD+-RW GSA-T21N
Version:        A102
Write speed:    706
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/scd0
------------------------------
Error: "/var/tmp/kdecache-copitox" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-copitox" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-copitox" is owned by uid 1000 instead of uid 0.


```

Does someone know how to run it ok without being root?

thanks!

PS: Sorry my bad english, i'm from southamerica.

PS2: Solved it running sudo chmod 777 /dev/scd0 but it might be dangerous or not good at all.

PS3: With the solution on PS2 it crashes in the middle of an iso recording, at still not working as it should.

PS4: Fixed it by creating another user, strange thing. Im gonna try if it still works after deleting that new user.

---

