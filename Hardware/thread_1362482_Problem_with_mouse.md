---
title: "Problem with mouse"
date: 2009-12-23
forum: Hardware
---

### Post by kounabi on 2009-12-23
Hello people!!

I have a logitech usb mouse and a laptop...if I plug the mouse before boot it works fine but if I plug it in after boot although I can see it with the lsusb command it doesn't work....
I've noticed that in /dev/input I have mice mouse0 and mouse1, but if I plug it in before boot I have mouse2 too...

I use ubuntu 9.10 and my kernel version is 2.6.31-16-generic.For further information please ask anything....

---

### Post by IcarusR on 2009-12-23
Which Logitech mouse, is wired or wireless ?

please post output of 

```
lsusb
```

---

### Post by kounabi on 2009-12-23
The mouse is wired but i don't remember the model now...

My lsusb output is

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c047 Logitech, Inc. Laser Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` 

....

---

### Post by kounabi on 2009-12-23
ok it can't be that difficult i guess...please anybody....

this is what dmesg shows when mouse is plugged before boot

```
[    2.076955] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.313032] usb 2-1: configuration #1 chosen from 1 choice
[    2.329605] usbcore: registered new interface driver hiddev
[    2.335376] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input5
[    2.335545] generic-usb 0003:046D:C047.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.0-1/input0

```

if it isn't plugged in only the first two lines appear and then nothing....

---

### Post by kounabi on 2010-03-01
I found out that when i plug in the mouse lshal shows the following:

```

19:47:45.143: usb_device_46d_c047_noserial added
19:47:45.149: usb_device_46d_c047_noserial_if0 added

```

why it adds two devices?
this the lshal info for the two devices:
```

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c047_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'  (string)
  info.product = 'Laser Mouse'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c047_noserial'  (string)
  info.vendor = 'Logitech, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/002/010'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 10016  (0x2720)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 10  (0xa)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Laser Mouse'  (string)
  usb_device.product_id = 49223  (0xc047)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Logitech, Inc.'  (string)
  usb_device.vendor_id = 1133  (0x46d)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c047_noserial_if0'
  info.linux.driver = 'ndiswrapper'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c047_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c047_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 10016  (0x2720)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 10  (0xa)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 49223  (0xc047)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 2.0 (2) (double)

```

Is this right?

---

### Post by kounabi on 2010-04-07
i finally found out that i didn't run the usbhid module at startup...everything works fine...

---

