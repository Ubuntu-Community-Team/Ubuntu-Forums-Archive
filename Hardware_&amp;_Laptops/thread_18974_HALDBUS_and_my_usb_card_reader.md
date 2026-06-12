---
title: "HAL/DBUS and my usb card reader"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by DrTiger on 2005-03-09
My cardreader doesn't work. I don't know how to activate dbus and hal on startup, but /etc/init.d/dbus restart says hal is running already. But gnome-volume-manager and hal-device-manager both say from time to time, that hal isn't running. Also I could never run both of them at the same time. When hal-device-manager starts successfully, it displays all the usb devices I plugged in, including the scsi one corresponding to the usb mass storage (a 128 mb card).
In hal-device-manager puts out the following, when plugging in the usb card reader:

```
DeviceAdded, udi=/org/freedesktop/Hal/devices/usb_device_7cc_330_5_-1_616853328837

DeviceAdded, udi=/org/freedesktop/Hal/devices/usb_usb_device_7cc_330_5_-1_616853328837_0

DeviceAdded, udi=/org/freedesktop/Hal/devices/scsi_host_21

DeviceAdded, udi=/org/freedesktop/Hal/devices/scsi_21_0_0_0
Exception dbus_bindings.DBusException: 'Message did not receive a reply' in 'dbus_bindings.cmessage_function_handler' ignored

DeviceAdded, udi=/org/freedesktop/Hal/devices/block_8_0
Exception dbus_bindings.DBusException: 'Message did not receive a reply' in 'dbus_bindings.cmessage_function_handler' ignored

```

Thanks for reading

---

### Post by DrTiger on 2005-03-10
I figured out, that there's a device /dev/sda1 that is created when I plug in the reader or the camera. However, it isn't mounted automatically, I have to mount i manually.

---

