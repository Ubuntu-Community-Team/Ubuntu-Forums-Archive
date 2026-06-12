---
title: "Auto mount usb hdd in fluxbox"
date: 2008-05-29
forum: Hardware
---

### Post by lexlex on 2008-05-29
Hi. I use xubuntu+fluxbox+ivman.
Do this 
[http://ubuntuforums.org/showthread.php?t=804777](http://ubuntuforums.org/showthread.php?t=804777)
I plug usb hdd, but folder /media is empty.

```
aus@aus-desktop:~$ ivman -d
manager.c:1387 (do_startup_configure) Directory /home/aus/.ivman/ will be used for configuration files.
manager.c:450 (ivm_test_configs) Settings directory does not exist, attempting to create it...
manager.c:786 (ivm_run_command) Running: /bin/mkdir -p /home/aus/.ivman/
manager.c:505 (ivm_test_configs) Configuration file /home/aus/.ivman/IvmConfigActions.xml not found, creating one with default content...
manager.c:505 (ivm_test_configs) Configuration file /home/aus/.ivman/IvmConfigBase.xml not found, creating one with default content...
manager.c:505 (ivm_test_configs) Configuration file /home/aus/.ivman/IvmConfigProperties.xml not found, creating one with default content...
manager.c:505 (ivm_test_configs) Configuration file /home/aus/.ivman/IvmConfigConditions.xml not found, creating one with default content...
manager.c:259 (set_mount_command) No mount command was specified in IvmConfigBase.xml.  Ivman will try to automatically detect the command to use. If Ivman incorrectly detects the program(s) available on your system, first make sure the program(s) are in the default shell PATH, then please report it as a bug.
manager.c:280 (set_mount_command) pmount-hal was found on your system. It will be used for mounting.
dbus_interface.c:108 (ivm_dbus_init) Connected to dbus
hal_interface.c:288 (hal_init) Initializing HAL
manager.c:1451 (main) ivman 0.6.14, http:/ivman.sourceforge.net
manager.c:1456 (main) Compiled against HAL 0.5.x or later
manager.c:1463 (main) Running in user mode.
manager.c:1501 (main) Entering main loop.
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial wasn't mounted, by us or by others...
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0 wasn't mounted, by us or by others...
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host wasn't mounted, by us or by others...
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host_scsi_device_lun0
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host_scsi_device_lun0 wasn't mounted, by us or by others...
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host_scsi_device_lun0_scsi_generic
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0_scsi_host_scsi_device_lun0_scsi_generic wasn't mounted, by us or by others...
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HC_0_0
IvmConfig/IvmConfigCommon.c:166 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HC_0_0 is device /dev/sdb
IvmConfig/IvmConfigCommon.c:186 (ivm_device_is_mountable) Device /dev/sdb can't be mounted because it is not a volume
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HC_0_0 wasn't mounted, by us or by others...
IvmConfig/IvmConfigCommon.c:166 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HC_0_0 is device /dev/sdb
IvmConfig/IvmConfigCommon.c:186 (ivm_device_is_mountable) Device /dev/sdb can't be mounted because it is not a volume
hal_interface.c:48 (hal_device_added) New Device: /org/freedesktop/Hal/devices/volume_uuid_52FC6280FC625DEB
IvmConfig/IvmConfigCommon.c:166 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_uuid_52FC6280FC625DEB is device /dev/sdb1
IvmConfig/IvmConfigCommon.c:227 (ivm_device_is_mountable) Device /dev/sdb1 won't be mounted because no mount policy was specified on volume or storage device and storage device does not appear to be removable
manager.c:1030 (ivm_media_changed) /org/freedesktop/Hal/devices/volume_uuid_52FC6280FC625DEB wasn't mounted, by us or by others...
IvmConfig/IvmConfigCommon.c:166 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_uuid_52FC6280FC625DEB is device /dev/sdb1
IvmConfig/IvmConfigCommon.c:227 (ivm_device_is_mountable) Device /dev/sdb1 won't be mounted because no mount policy was specified on volume or storage device and storage device does not appear to be removable
```
What I do wrong?

---

