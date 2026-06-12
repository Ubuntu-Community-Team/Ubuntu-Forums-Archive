---
title: "Help installing touch screen!"
date: 2011-09-01
forum: Hardware
---

### Post by kokomodrums on 2011-09-01
I have a Gateway CX2620. Here's some info i've found (im a ubuntu NEWB) 

(lshal | less)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input6/event6'  (string)




(can't remember what command got me this info)


[   22.207179] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008/0x0

[   22.396293] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6


The touchscreen does not work at all or respond to anything.

Any ideas on where to start (P.S. I'm an Ubuntu NEWB so I'm gonna need specific terminal commands if you can! Thanks!

---

