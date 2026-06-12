---
title: "Want to disable Touchpad when a USB Wireless Mouse is attached"
date: 2010-08-19
forum: Hardware
---

### Post by Casper34 on 2010-08-19
I have searched and tried a few different posts here and they seem to work, but only for a few minutes. I can turn my touch pad on and off using some scripts, but after i turn it off, after a few minutes it turns back on. 

My Laptop specs are:
TOSHIBA 
PSLB8U-13T038
Ubuntu 10.04LTS running Gnome

My device data when the mouse is plugged in is 

[PHP]udi = '/org/freedesktop/Hal/devices/usb_device_46d_c526_noserial_if1'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c526_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c526_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration = 'RQR05.00_B0023'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 1280  (0x500)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 50470  (0xc526)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 2.0 (2) (double)[/PHP]And

[PHP]udi = '/org/freedesktop/Hal/devices/usb_device_46d_c526_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c526_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c526_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration = 'RQR05.00_B0023'  (string)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 1280  (0x500)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 50470  (0xc526)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 2.0 (2) (double)[/PHP]Please someone help me, this is getting annoying and i like Ubuntu, i really dont want to go back to....... need i say it?

---

### Post by Casper34 on 2010-08-21
bump

---

### Post by Casper34 on 2010-08-25
im so glad people are helpful on this damn site..... 3 unanswered questions! Thanks!!!!!!!

---

