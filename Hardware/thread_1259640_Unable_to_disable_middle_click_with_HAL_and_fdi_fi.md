---
title: "Unable to disable middle click with HAL and fdi file"
date: 2009-09-06
forum: Hardware
---

### Post by ENOTTY on 2009-09-06
Hi, I am at my wit's end with this. I am trying to disable the middle click in my Synaptics touchpad because its way too easy to hit it on my eeepc. I've tried several different methods to no avail.

I know this can be done because I've done
```
xinput set-button-map "SynPS/2 Synaptics TouchPad" 1 0 3
```
and the middle click will stop triggering. I've verified this through watching xev and with ```
xinput get-button-map "SynPS/2 Synaptics TouchPad"
```

1. Setting up a policy through HAL and fdi. (Preferred option).
Here is the current incarnation of my fdi configuration file.
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
  <match key="info.product" contains="Synaptics TouchPad">
    <merge key="input.x11_driver" type="string">synaptics</merge>
    <merge key="input.x11_options.ButtonMapping" type="string">1 0 3</merge>
  </match>
</device>
</deviceinfo>

```
Restarted, and discovered that middle click still worked.

Also tried putting the following text in ~/.xsessionrc and ~/.xstartup.
```
#!/bin/sh

xinput set-button-map "SynPS/2 Synaptics TouchPad" 1 0 3

```
Restarted and the middle click button still worked so i guess these arent being sourced or something. 

Here is the relevant output from lshal. If anybody wants the full thing, just say so.
```
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.ButtonMapping = '1 0 3'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input10/event10'  (string)

```
So it seems the button mapping is getting set right in HAL, but it's still not being recognized...

Any help would be appreciated and TIA

---

### Post by miegiel on 2009-09-23
I'm struggeling with this too. It seems the *"input.x11_options.Buttons"* and *"input.x11_options.ButtonMapping"* don't work. They are also not listed as options in the man page.
```
man synaptics
```

What might do the trick for you is :

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
  <match key="info.product" contains="Synaptics TouchPad">
      <merge key="input.x11_options.TapButton1" type="string">1</merge>
      <merge key="input.x11_options.TapButton2" type="string">0</merge>
      <merge key="input.x11_options.TapButton3" type="string">3</merge>
  </match>
</device>
</deviceinfo>

```

I'm trying to accomplish something different though. I want to make the left button below the pad my middle mouse button.

---

