---
title: "Mount Canon Powershot SD600 (IXUS 60 in europe)"
date: 2008-06-21
forum: Hardware
---

### Post by putteb on 2008-06-21
Hi,

I'm wondering if it is possible to mount my camera file system so that I can browse the files on the flash disk without going through the f-spot import.

Here's the diff of lshal between camera unplugged/plugged:

```
< Dumping 99 device(s) from the Global Device List:
---
> Dumping 97 device(s) from the Global Device List:
879,952d878
< udi = '/org/freedesktop/Hal/devices/usb_device_4a9_311c_noserial'
<   info.bus = 'usb_device'  (string)
<   info.linux.driver = 'usb'  (string)
<   info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_10_4'  (string)
<   info.product = 'Canon Digital Camera'  (string)
<   info.subsystem = 'usb_device'  (string)
<   info.udi = '/org/freedesktop/Hal/devices/usb_device_4a9_311c_noserial'  (string)
<   info.vendor = 'Canon, Inc.'  (string)
<   linux.device_file = '/dev/bus/usb/005/005'  (string)
<   linux.hotplug_type = 2  (0x2)  (int)
<   linux.subsystem = 'usb'  (string)
<   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.4/usb5/5-6'  (string)
<   usb_device.bus_number = 5  (0x5)  (int)
<   usb_device.can_wake_up = false  (bool)
<   usb_device.device_class = 0  (0x0)  (int)
<   usb_device.device_protocol = 0  (0x0)  (int)
<   usb_device.device_revision_bcd = 2  (0x2)  (int)
<   usb_device.device_subclass = 0  (0x0)  (int)
<   usb_device.is_self_powered = false  (bool)
<   usb_device.linux.device_number = 5  (0x5)  (int)
<   usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.4/usb5/5-6'  (string)
<   usb_device.num_configurations = 1  (0x1)  (int)
<   usb_device.num_ports = 0  (0x0)  (int)
<   usb_device.product = 'Canon Digital Camera'  (string)
<   usb_device.product_id = 12572  (0x311c)  (int)
<   usb_device.speed = 480.0 (480) (double)
<   usb_device.speed_bcd = 294912  (0x48000)  (int)
<   usb_device.vendor = 'Canon, Inc.'  (string)
<   usb_device.vendor_id = 1193  (0x4a9)  (int)
<   usb_device.version = 2.0 (2) (double)
<   usb_device.version_bcd = 512  (0x200)  (int)
< 
< udi = '/org/freedesktop/Hal/devices/usb_device_4a9_311c_noserial_if0'
<   access_control.file = '/dev/bus/usb/005/005'  (string)
<   access_control.type = 'camera'  (string)
<   camera.access_method = 'ptp'  (string)
<   camera.libgphoto2.name = 'USB PTP Class Camera'  (string)
<   camera.libgphoto2.support = true  (bool)
<   info.bus = 'usb'  (string)
<   info.callouts.add = {'hal-acl-tool --add-device'} (string list)
<   info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
<   info.capabilities = {'camera', 'camera', 'camera', 'camera', 'access_control'} (string list)
<   info.category = 'camera'  (string)
<   info.parent = '/org/freedesktop/Hal/devices/usb_device_4a9_311c_noserial'  (string)
<   info.product = 'USB Imaging Interface'  (string)
<   info.subsystem = 'usb'  (string)
<   info.udi = '/org/freedesktop/Hal/devices/usb_device_4a9_311c_noserial_if0'  (string)
<   linux.hotplug_type = 2  (0x2)  (int)
<   linux.subsystem = 'usb'  (string)
<   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.4/usb5/5-6/5-6:1.0'  (string)
<   usb.bus_number = 5  (0x5)  (int)
<   usb.can_wake_up = false  (bool)
<   usb.device_class = 0  (0x0)  (int)
<   usb.device_protocol = 0  (0x0)  (int)
<   usb.device_revision_bcd = 2  (0x2)  (int)
<   usb.device_subclass = 0  (0x0)  (int)
<   usb.interface.class = 6  (0x6)  (int)
<   usb.interface.number = 0  (0x0)  (int)
<   usb.interface.protocol = 1  (0x1)  (int)
<   usb.interface.subclass = 1  (0x1)  (int)
<   usb.is_self_powered = false  (bool)
<   usb.linux.device_number = 5  (0x5)  (int)
<   usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.4/usb5/5-6/5-6:1.0'  (string)
<   usb.num_configurations = 1  (0x1)  (int)
<   usb.num_ports = 0  (0x0)  (int)
<   usb.product = 'USB Imaging Interface'  (string)
<   usb.product_id = 12572  (0x311c)  (int)
<   usb.speed = 480.0 (480) (double)
<   usb.speed_bcd = 294912  (0x48000)  (int)
<   usb.vendor = 'Canon, Inc.'  (string)
<   usb.vendor_id = 1193  (0x4a9)  (int)
<   usb.version = 2.0 (2) (double)
<   usb.version_bcd = 512  (0x200)  (int)
< 
2247c2173
< Dumped 99 device(s) from the Global Device List.
---
> Dumped 97 device(s) from the Global Device List.

```

I tried 
**sudo mount /dev/bus/usb/005/005 /mnt/** 
but then i get
**mount: /dev/bus/usb/005/005 is not a block device**

Ideas?

---

### Post by naught101 on 2009-12-12
Good question. I'd also like to know this.

---

### Post by IcarusR on 2009-12-12
Simplest way may be to use a USB card reader. Which is what I always do.

---

