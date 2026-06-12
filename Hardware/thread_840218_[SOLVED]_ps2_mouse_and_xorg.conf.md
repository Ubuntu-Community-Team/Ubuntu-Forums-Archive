---
title: "[SOLVED] ps/2 mouse and xorg.conf"
date: 2008-06-25
forum: Hardware
---

### Post by kessaris on 2008-06-25
Hello all!

It's a great pleasure to be using ubuntu, this is just the beginning of my career with this great operating system!

That being said, my current installation of Hardy Heron is working absolutely marvelously with my Sharp PC-XV70G laptop (Japanese), save for a few small quirks.

Most notably!! The built in touchpad is not being configured correctly.  I have done a lot of research about this problem, many people are reporting issues with the 2.6 kernel and PS/2 Devices.

I am starting this thread in the hope of solving some of these problems!

Here is the basic info.  The mouse seems to be a PS/2 device.  I have managed to locate it using hwinfo.  Below is the relevant output:

```
  53: udi = '/org/freedesktop/Hal/devices/pnp_PNP0f03'
  linux.sysfs_path = '/sys/devices/pnp0/00:01'
  info.subsystem = 'pnp'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'Microsoft PS/2-style Mouse'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f03'
  info.linux.driver = 'i8042 aux'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0f03'
  linux.subsystem = 'pnp'
  pnp.description = 'Microsoft PS/2-style Mouse'
```

Unfortunately, this device is not being accessed by the O/S.  Instead, it seems that this virtual device is being attached to the event system:

```
16: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  input.device = '/dev/input/event0'
  input.product = 'Macintosh mouse button emulation'
  linux.sysfs_path = '/sys/devices/virtual/input/input0/event0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.product = 'Macintosh mouse button emulation'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  info.category = 'input'
  linux.hotplug_type = 2 (0x2)
  info.capabilities = { 'input', 'input.mouse' }
  linux.subsystem = 'input'
  linux.device_file = '/dev/input/event0'
```

I suspect it has something to do with the move to the new /sys directory structure, but in all honesty I don't know enough about linux or ubuntu to say for sure.

My question is then:  How would one connect the correct device to the appropriate driver and get it working with xorg?

In xorg.conf I've just got the default data:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```

Any help is appreciated!

---

### Post by kessaris on 2008-06-30
It's all sorted out!  I have posted my findings here:

[http://ubuntuforums.org/showthread.php?t=844968](http://ubuntuforums.org/showthread.php?t=844968)

---

