---
title: "Set Touchpad Properties Using HAL"
date: 2009-01-05
forum: Hardware
---

### Post by Manslen on 2009-01-05
Hi there,

I've wanted to change the default settings of my touchpad (Dell D630, ALPS touchpad). I am able to do so with synclient, but would like to have it done on startup (also, there is no reason to leave SHMConfig on). I found one post which describes a workaround using synclient & SHMConfig 

I've looked through the [Ubuntu Wiki]("https://wiki.ubuntu.com/X/Config/Input") & [several]("http://ubuntuforums.org/showthread.php?t=968668") [similar]("http://ubuntuforums.org/showthread.php?t=948154") [posts]("http://ubuntuforums.org/showthread.php?t=1019027") & [pages]("https://help.ubuntu.com/community/Wacom.fdi"). I created the following and fdi that sets the "MaxSpeed", "MinSpeed" & "AccelFactor" of my touchpad. This fdi is successfully invoked, since lshal shows these properties as set:

```

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_inp
ut_0'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_option.AccelFactor = '0.4'  (string)
  input.x11_option.MaxSpeed = '1.0'  (string)
  input.x11_option.MinSpeed = '0.6'  (string)
  input.x11_options.SHMConfig = 'True'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input13/event11' (string)

```

However, no visible touchpad behaviour has changed.

my xorg.conf:
```

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Any help on correctly applying these settings would be appreciated.

---

