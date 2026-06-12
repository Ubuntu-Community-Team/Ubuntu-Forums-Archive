---
title: "display problem of vaio f12 series with maverick amd64"
date: 2010-11-12
forum: Hardware
---

### Post by etsunan-jin on 2010-11-12
Last month I bought a Vaio VPCF12JFX. I have installed maverick amd64 and config nvidia card to disable noveau and use nvidia driver 256.53. Here's my xorg.conf
> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
#    InputDevice    "Synaptics" "SendCoreEvents"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver  "synaptics"
        Option  "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizEdgeScroll" "0"
        Option "SHMConfig" "1"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


There are some serious problem :
- When I press "displayoff" button on keyboard or idle for 5 minutes, the display was turned off, but when I touch to keyboard or mouse, the monitor only turned on for few seconds with darkened backlight, then turned off. There are no way to fix it, so I have to reboot system.
- Maverick can't recognize my touchpad (ALPS pointing device). Touchpad only works when I add ```
GRUB_CMDLINE_LINUX="i8042.nopnp"
``` to  /etc/default/grub but it hasn't got multitouch feature. Maverick only recognize my touchpas as an 'regular' ImPS2 mouse. I have tried to enable SHMconfig and install xserver-xorg-input-synaptics as a manual I have read [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig"), but it doesn't work. Here is lshal entry :
> 
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  info.product = 'ImPS/2 Generic Wheel Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  input.product = 'ImPS/2 Generic Wheel Mouse'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio2/input/input8/event8'  (string)
and here is synclient output
> huy@huy-laptop:~$ synclient -m 100
Can't access shared memory area. SHMConfig disabled?


Anyone can tell me how to solve there problems? Thank you very much! (Sorry about my English)

---

