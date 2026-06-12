---
title: "Binding a script to a switch previously handled by hal"
date: 2010-06-01
forum: Hardware
---

### Post by mooware on 2010-06-01
Hi there,

I have an Intel Classmate Convertible netbook, on which I recently installed Lucid. This being a convertible, I can turn the display around to make it a pseudo-tablet, so that the display lies flat on the keyboard, but looks outside. This should trigger a hardware switch that I would like to use to enable and disable autorotation of the screen. On Karmic, hal recognized this switch as follows:

```

14: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_8'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/TBLT0000:00/input/input9/event9'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.category = 'input'  (string)
  info.capabilities = { 'input', 'input.switch', 'button' } (string list)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  input.device = '/dev/input/event9'  (string)
  input.product = 'cmpc_tablet'  (string)
  button.has_state = true  (bool)
  info.product = 'cmpc_tablet'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_8'  (string)
  button.state.value = false  (bool)
  info.addons.singleton = { 'hald-addon-input' } (string list)
  button.type = 'tablet_mode'  (string)
  info.subsystem = 'input'  (string)

```I already found out that this device is available as [FONT=Courier New]/dev/input/event8[/FONT] on my system, because running [FONT=Courier New]sudo cat /dev/input/event8[/FONT] prints some garbage characters exactly when I switch in or out of tablet mode.

How can I bind a script to this switch?

UPDATE:
By using input-events from the package input-utils, I can actually receive events from the switch. It gives me the following for closing and opening the display:

```

/dev/input/event8
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "cmpc_tablet"
   bits ev : EV_SYN EV_SW

waiting for events
17:44:16.915878: EV_SW code=1 value=1
17:44:19.627890: EV_SW code=1 value=0

```

And the same with evtest:

```

Input driver version is 1.0.0
Input device ID: bus 0x0 vendor 0x0 product 0x0 version 0x0
Input device name: "cmpc_tablet"
Supported events:
  Event type 0 (Sync)
  Event type 5 (?)
    Event code 1 (?)
Testing ... (interrupt to exit)
Event: time 1275493997.571895, type 5 (?), code 1 (?), value 1
Event: time 1275494001.279872, type 5 (?), code 1 (?), value 0

```

Still, I don't know how to do something with it other than writing a script to use input-events.

---

