---
title: "problem with Qualcomm 9201 WWAN card"
date: 2009-03-27
forum: Hardware
---

### Post by wirelessmonk on 2009-03-27
I have a Thinkpad T500 that I've been struggling with lately.  I'm trying to get my Qualcomm 9201 WWAN card (mini-pci) to work with my Verizon data plan.

I started out with 8.10, but just installed 9.04 beta in the hopes that the support would magically be there... it wasn't :)

The issue is, I'm not exactly sure where I should be looking for the problem.  While I'm not exactly new to Linux, I am totally new to using WWAN cards with Linux...

here's my relevant info:

Thinkpad T500
Ubuntu J.J. beta
Qualcomm 9201 WWAN card on Verizon.

lsusb
```
Bus 008 Device 002: ID 05c6:9201 Qualcomm, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 04b3:4485 IBM Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0a5c:2145 Broadcom Corp. 
Bus 002 Device 004: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lshal (relevant entries)
```
udi = '/org/freedesktop/Hal/devices/usb_device_5c6_9201_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'  (str
ing)
  info.product = 'Qualcomm HS-USB'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5c6_9201_noserial'  (string)
  info.vendor = 'Qualcomm, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/008/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb8/8-4'  (string)
  usb_device.bus_number = 8  (0x8)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 1  (0x1)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb8/8-4'  (s
tring)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Qualcomm HS-USB'  (string)
  usb_device.product_id = 37377  (0x9201)  (int)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Qualcomm, Inc.'  (string)
  usb_device.vendor_id = 1478  (0x5c6)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5c6_9201_noserial_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5c6_9201_noserial'  (strin
g)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5c6_9201_noserial_if0'  (stri
ng)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb8/8-4/8-4:1.0'  (stri
ng)
  usb.bus_number = 8  (0x8)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 1  (0x1)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 255  (0xff)  (int)
  usb.interface.subclass = 255  (0xff)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb8/8-4/8-4:1.0'  (
string)
  usb.max_power = 500  (0x1f4)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 37377  (0x9201)  (int)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Qualcomm, Inc.'  (string)
  usb.vendor_id = 1478  (0x5c6)  (int)
  usb.version = 2.0 (2) (double)
```

uname -r
```
2.6.28-11-generic
```


I've input all my info into NetworkManager, but it doesn't seem to see the modem.  

I've also installed a copy of the Linux version of VZAccess Manager but it doesn't see the device either.

Gnome-ppp.... guess what... didn't see the device.


Does anyone have any ideas what I should be checking here?

Thanks!

---

### Post by wirelessmonk on 2009-03-29
sorry to bump, but this thread made it all the way down to page 12...  :)  Didn't want it to get lost...

Thanks.

---

