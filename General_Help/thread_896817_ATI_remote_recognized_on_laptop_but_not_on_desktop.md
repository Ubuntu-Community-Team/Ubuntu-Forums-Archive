---
title: "ATI remote recognized on laptop but not on desktop?"
date: 2008-08-21
forum: General Help
---

### Post by kwilliam on 2008-08-21
I've got an ATI HDTV Wonder Remote that I want to use with MythTV. When I plugged the USB adaptor into my laptop, it worked out-of-the-box with no configuration needed: Arrow keys moved mouse, numbers entered numbers, etc. However, on the fresh installation of Kubuntu 8.04 on the desktop I built for MythTV, the remote doesn't work. The kernel SEES the remote, and knows it's name, but none of the buttons work. Inspecting with kde-hal-device-manager, I notice that the laptop sees a little more detail than the desktop does.

The desktop sees:
```
> USB 1.1 Controller
  > OHCI Host Controller
    > USB Hub Interface
    > USB Vendor Specific Interface
    > X10 Receiver
```
The laptop sees:
```
> 82801G (ICH7 Family) USB UHCI Controller #4
  > UHCI Host Controller
    > USB Hub Interface
    > X10 Receiver
      > USB Vendor Specific Interface
      > X10 Wireless Technology Inc USB Receiver
```

I'm baffled because both the laptop and the new desktop have up-to-date Kubuntu 8.04 installations, only the desktop install is brand new, while the laptop has been upgraded since Feisty. If anybody has an explanation, or an idea that might get the remote to work with the desktop (I built it to be a MythTV box) I'd appreciate it.

I don't know whether it's HAL or what, but here's how HAL sees the remote on my laptop (where it works):
```
udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'  (string)
  info.product = 'X10 Receiver'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'  (string)
  info.vendor = 'X10 Wireless Technology, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/004/006'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1'  (string)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'X10 Receiver'  (string)
  usb_device.product_id = 4  (0x4)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.speed_bcd = 336  (0x150)  (int)
  usb_device.vendor = 'X10 Wireless Technology, Inc.'  (string)
  usb_device.vendor_id = 3015  (0xbc7)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'  (string)
  info.product = 'X10 Wireless Technology Inc USB Receiver'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'  (string)
  input.product = 'X10 Wireless Technology Inc USB Receiver'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'evdev'  (string)
  input.xkb.rules = 'base'  (string)
  input.xkb.variant = ''  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1/input/input13/event11'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'ati_remote'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'  (string)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 4  (0x4)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.speed_bcd = 336  (0x150)  (int)
  usb.vendor = 'X10 Wireless Technology, Inc.'  (string)
  usb.vendor_id = 3015  (0xbc7)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)
```

Here's what HAL sees on the desktop:
```
udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_0'  (string)
  info.product = 'X10 Receiver'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'  (string)
  info.vendor = 'X10 Wireless Technology, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/001/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-2'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-2'  (string)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'X10 Receiver'  (string)
  usb_device.product_id = 4  (0x4)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.speed_bcd = 336  (0x150)  (int)
  usb_device.vendor = 'X10 Wireless Technology, Inc.'  (string)
  usb_device.vendor_id = 3015  (0xbc7)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'lirc_atiusb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial'  (string)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_bc7_4_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.0'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 4  (0x4)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.speed_bcd = 336  (0x150)  (int)
  usb.vendor = 'X10 Wireless Technology, Inc.'  (string)
  usb.vendor_id = 3015  (0xbc7)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)
```
  
It looks like it's missing the logical input device portion. Any idea what's going wrong or how I can get the remote to work with the desktop?

---

### Post by kwilliam on 2008-08-21
It occurred to me to post dmesg results.

Laptop dmesg | tail:
```
[11617.210586] sd 3:0:0:0: Attached scsi generic sg2 type 0
[11631.907530] usb 4-1: new low speed USB device using uhci_hcd and address 7
[11632.081719] usb 4-1: configuration #1 chosen from 1 choice
[11634.117268] input: X10 Wireless Technology Inc USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/input/input12
[11632.120576] /build/buildd/linux-2.6.24/drivers/input/misc/ati_remote.c: Weird data, len=1 ff 3e 79 f0 00 00 ...

```

Now, despite it saying "Weird data", it works. The one below, which seems to load more ati specific modules, is the one that *doesn't* work.

Desktop dmesg | tail:
```
[   55.123385] eth0: no IPv6 routers present
[  118.640141] usb 3-1: new low speed USB device using ohci_hcd and address 2
[  118.746943] usb 3-1: configuration #1 chosen from 1 choice
[  118.830272] lirc_dev: IR Remote Control driver registered, at major 61 
[  118.833812] 
[  118.833814] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[  118.833817] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[  118.836427] lirc_dev: lirc_register_plugin: sample_rate: 0
[  118.839188] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb3:2
[  118.845700] usbcore: registered new interface driver lirc_atiusb
[  118.854709] usbcore: registered new interface driver ati_remote
[  118.854872] /build/buildd/linux-2.6.24/drivers/input/misc/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1

```

---

