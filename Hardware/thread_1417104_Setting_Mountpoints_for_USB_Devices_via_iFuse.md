---
title: "Setting Mountpoints for USB Devices via iFuse"
date: 2010-02-26
forum: Hardware
---

### Post by mastermindg on 2010-02-26
This is related to the iPhone/iPod sync but my issue is solely one of hardware detection at this point:

lshal -u $(hal-find-by-property --key "info.vendor" --string "Apple, Inc.")
udi = '/org/freedesktop/Hal/devices/usb_device_5ac_1293_ce78b6b40dd452fe5b8a3c05fd245ec68468e866'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_0b_1'  (string)
  info.product = 'iPod'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5ac_1293_ce78b6b40dd452fe5b8a3c05fd245ec68468e866'  (string)
  info.vendor = 'Apple, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/001/005'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.1/usb1/1-8'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration = 'PTP + Apple Mobile Device'  (string)
  usb_device.configuration_value = 3  (0x3)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 1  (0x1)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 5  (0x5)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.1/usb1/1-8'  (string)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_configurations = 3  (0x3)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'iPod'  (string)
  usb_device.product_id = 4755  (0x1293)  (int)
  usb_device.serial = 'ce78b6b40dd452fe5b8a3c05fd245ec68468e866'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Apple, Inc.'  (string)
  usb_device.vendor_id = 1452  (0x5ac)  (int)
  usb_device.version = 2.0 (2) (double)

I'm able to mount this device via ifuse. I'd like to be able to setup an automatic mountpoint of my choice rather than the default mountpoint of /home/$USER/.gvfs. I'm not familiar enough with the mechanisms here. Please give me a rundown on I need to do to get this added to fstab or alter the gvfs configuration...

---

