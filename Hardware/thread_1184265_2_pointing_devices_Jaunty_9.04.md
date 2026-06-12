---
title: "2 pointing devices Jaunty 9.04"
date: 2009-06-11
forum: Hardware
---

### Post by vayira on 2009-06-11
I normally use two pointing devices...
1. ps/2 egonomic mouse
2. usb wireless scroll wheel mouse

So far every o/s I have ever used lets me use both at once, but for some reason Jaunty won't. I just installed it. 

If I hotplug the usb mouse *dmesg* shows me that mouse is recognised, but it doesn't do anything. Then *lshal | grep "Mouse"* gives...

[I]  info.product = 'Microsoft PS/2-style Mouse'  (string)
  pnp.description = 'Microsoft PS/2-style Mouse'  (string)
  info.product = 'PS/2 Generic Mouse'  (string)
  input.product = 'PS/2 Generic Mouse'  (string)
  hiddev.product = 'Mlk              Cordless USB Mouse & Keyboard'  (string)
  info.product = 'Mlk              Cordless USB Mouse & Keyboard'  (string)[/I]

Not quite sure how to get it going. What does hiddev mean in hal? 

All suggestions welcome.

---

### Post by vayira on 2009-06-11
Here is the complete lshal listing for the device that doesn't work. I only have a vague idea how hal works so any help would be very much appreciated...

[INDENT][I]udi = '/org/freedesktop/Hal/devices/usb_device_419_1_noserial_if0_hiddev'
  hiddev.application_pages = {'Generic Desktop Page', 'Generic Desktop Page', 'Generic Desktop Page'} (string list)
  hiddev.device = '/dev/usb/hiddev0'  (string)
  hiddev.product = 'Mlk              Cordless USB Mouse & Keyboard'  (string)
  info.capabilities = {'hiddev'} (string list)
  info.category = 'hiddev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_419_1_noserial_if0'  (string)
  info.product = 'Mlk              Cordless USB Mouse & Keyboard'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_419_1_noserial_if0_hiddev'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/usb/hiddev0'  (string)[/I][/INDENT]

I continue exploring the web, but don't still can't find any info that helps me understand what to do.

---

