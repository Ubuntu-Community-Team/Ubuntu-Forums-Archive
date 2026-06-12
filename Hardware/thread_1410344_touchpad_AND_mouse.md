---
title: "touchpad AND mouse?"
date: 2010-02-18
forum: Hardware
---

### Post by ronti69 on 2010-02-18
I have just made my Microsoft Intellimouse work on my laptop by using HAL configuration as described in 

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

It worked right away. I can actually create 2 fdi files for 2 different mice, and they both work. However, the touchpad stopped working. If I start the computer with the mouse unplugged, then the touchpad works fine... but the mouse doesn't.
Is there a way to have them both working at the same time?

thanks!

---

### Post by ronti69 on 2010-02-18
Sorry, forgot to say I am using Ubuntu 9.10 on an HP Pavillion tx 2000

---

### Post by pi/roman on 2010-02-18
Could you post your HAL configuration files and also your xorg.conf file at /etcX11/xorg.conf if it exists please?

---

### Post by ronti69 on 2010-02-18
This is the xorg.conf file:

[I][SIZE="2"][HTML]Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2176 790
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection[/HTML][/SIZE][/I]

This is the fdi file that I created to configure the mouse. There are no other fdi files at /etc/hal/fdi/policy

[I][SIZE="1"][HTML]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_driver" type="string">mouse</merge>

    <!-- Logitech tweaks -->
    <match key="@input.originating_device:usb.045e" int="0x46d">
     <match key="@input.originating_device:usb.0059" int_outof="0xc50e;0xc518">
      <merge key="input.x11_options.RelHWHEELOptions" type="string">invert</merge>
     </match>
    </match>

   </match>
  </match>
 </device>
</deviceinfo>[/HTML][/I][/SIZE]

---

### Post by pi/roman on 2010-02-18
The xorg.conf is good and the fdi is ok except you have 3 match key opens and 4 match key closes but I don't think that would be causing your problem so delete one of them but you will probably need a synaptics fdi.
If you post the output of this:
```
lshal -s | grep i8042 | xargs -n1 lshal -u
```it would help.

---

### Post by ronti69 on 2010-02-18
Thanks pi/roman. Here's the output:

[SIZE="1"]```
udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event13'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.HorizTwoFingerScroll = 'true'  (string)
  input.x11_options.VertTwoFingerScroll = 'true'  (string)
  linux.device_file = '/dev/input/event13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input13/event13'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input5/event5'  (string)

```[/SIZE]

---

### Post by pi/roman on 2010-02-18
You can create a file in /etc/hal/fdi/policy/ called 11-x11-synaptics.fdi by:
```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```paste the following into it and reboot, your touchpad should be working properly.
[HTML]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="SynPS/2 Synaptics TouchPad">
    <merge key="input.x11_driver" type="string">synaptics</merge>
    <merge key="input.x11_options.SHMConfig" type="string">on</merge>
        <!-- EXAMPLES:
    Maximum movement of the finger for detecting a tap
    <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

    Enable vertical scrolling when dragging along the right edge
    <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

    Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

    Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

    If on, circular scrolling is used
    <merge key="input.x11_options.CircularScrolling" type="string">true</merge>

    For other possible options, check CONFIGURATION DETAILS in "man synaptics" page-->
    </match>
  </device>
</deviceinfo>[/HTML]

---

### Post by ronti69 on 2010-02-19
Thanks. I did that and it got the touchpad to work... but it killed the mouse...
So I deleted /etc/hal/fdi/policy/11-x11-synaptics.fdi and rebooted, but still only the touchpad works.
I don't understand... shouldn't deleting that file take me back to where I was before, that is, the mouse working and the touchpad not? The fdi file for the mouse is still there...so what changed? What did /etc/hal/fdi/policy/11-x11-synaptics.fdi do that cannot be undone by deleting it and rebooting?

Anyways, I am trying not only to get them both to work, but also learn something about how the system works... I am a total beginner as you must have guessed

---

### Post by pi/roman on 2010-02-19
It may be your mouse that needs to be reconfigured.  You can change your mouse.fdi to mouse.bkp then make an empty mouse.fdi and paste the following into it:

[HTML]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_driver" type="string">evdev</merge>
  </match>
 </device>
</deviceinfo>[/HTML]

---

### Post by ronti69 on 2010-02-19
nope... still touchpad only unfortunately

if I delete the fdi for the touchpad, shouldn't the mouse work again?

---

### Post by pi/roman on 2010-02-19
Changing the synaptics configuration should have no effect on the mouse unless they are both strapped on to the same driver interface. Try commenting out your old fdi by putting this <!-- on the top line. Then restart and plug in your mouse and do this:
```
tail -31 /proc/bus/input/devices
```Also run this command with your mouse plugged in:
```
lshal lshal -s | grep logicaldev_input | xargs -n1 lshal -u
```

---

### Post by ronti69 on 2010-02-19
The tail command gave me this:

[SIZE="2"]```
P: Phys=usb-0000:00:12.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input14
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=10000 7 ff980000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0a81 Product=0205 Version=0110
N: Name="CHESEN PS2 to USB Converter"
P: Phys=usb-0000:00:12.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input15
U: Uniq=
H: Handlers=kbd mouse1 event8 
B: EV=17
B: KEY=1f001f 0 2020000 3878 d801d001 1e0000 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=045e Product=0059 Version=0110
N: Name="Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A"
P: Phys=usb-0000:00:12.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input16
U: Uniq=
H: Handlers=mouse5 event14 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```[/SIZE]


The same command, but with the mouse unplugged:

[SIZE="2"]```
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse4 event13 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0003 Vendor=0a81 Product=0205 Version=0110
N: Name="CHESEN PS2 to USB Converter"
P: Phys=usb-0000:00:12.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input17
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=10000 7 ff980000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0a81 Product=0205 Version=0110
N: Name="CHESEN PS2 to USB Converter"
P: Phys=usb-0000:00:12.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input18
U: Uniq=
H: Handlers=kbd mouse1 event8 
B: EV=17
B: KEY=1f001f 0 2020000 3878 d801d001 1e0000 0 0 0
B: REL=103
B: MSC=10

```[/SIZE]


The lshal command (mouse plugged):

[SIZE="2"]```
udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  button.has_state = false  (bool)
  button.type = 'sleep'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Sleep Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Sleep Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Power Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Power Button'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Video Bus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.product = 'Video Bus'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6/event6'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'
  button.has_state = true  (bool)
  button.state.value = false  (bool)
  button.type = 'lid'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.switch', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Lid Switch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'  (string)
  input.device = '/dev/input/event3'  (string)
  input.product = 'Lid Switch'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'  (string)
  input.device = '/dev/input/event4'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/input/event13'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  linux.device_file = '/dev/input/event13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input13/event13'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1'  (string)
  info.product = 'Wacom ISDv4 93'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1'  (string)
  input.product = 'Wacom ISDv4 93'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input11/event11'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input'  (string)
  info.product = 'Wacom ISDv4 93 pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event11'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input'  (string)
  info.product = 'Wacom ISDv4 93 cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event11'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input'  (string)
  info.product = 'Wacom ISDv4 93 eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if1_logicaldev_input_subdev'  (string)
  input.device = '/dev/input/event11'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0'  (string)
  info.product = 'Wacom ISDv4 93'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0'  (string)
  input.product = 'Wacom ISDv4 93'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input10/event10'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom ISDv4 93 pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event10'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom ISDv4 93 cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event10'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom ISDv4 93 eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0_logicaldev_input_subdev'  (string)
  input.device = '/dev/input/event10'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  info.product = 'HDA Digital PCBeep'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_logicaldev_input'  (string)
  input.device = '/dev/input/event12'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  input.product = 'HDA Digital PCBeep'  (string)
  linux.device_file = '/dev/input/event12'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/input/input12/event12'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_4f2_b103_SN0001_if0_logicaldev_input'
  button.has_state = false  (bool)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'button', 'input.keys'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_4f2_b103_SN0001_if0'  (string)
  info.product = 'CKF7073'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_4f2_b103_SN0001_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_4f2_b103_SN0001_if0'  (string)
  input.product = 'CKF7073'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input9/event9'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_if0'  (string)
  info.product = 'Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event14'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_if0'  (string)
  input.product = 'Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event14'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input16/event14'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if1_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if1'  (string)
  info.product = 'CHESEN PS2 to USB Converter'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if1'  (string)
  input.product = 'CHESEN PS2 to USB Converter'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input15/event8'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if0'  (string)
  info.product = 'CHESEN PS2 to USB Converter'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_a81_205_noserial_if0'  (string)
  input.product = 'CHESEN PS2 to USB Converter'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input14/event7'  (string)

```[/SIZE]

---

### Post by pi/roman on 2010-02-19
That looks good so I don't know what to think. You can try your original fdi again if you want.
The following would be good to look at when the mouse is plugged in, more of the same lshal output but it should be trimmed down as good as it can be to the usb mouse tree:
```
lshal lshal -s | grep usb_device_45e_59_noserial | xargs -n1 lshal -u
```Also check xinput settings:
```
xinput list | grep -i mouse | grep -o '"[^"]*"' | xargs xinput list-props
```

---

### Post by Ayuthia on 2010-02-19
You might try the following:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_driver" type="string">mouse</merge>
  </match>
 </device>
</deviceinfo>

```

pi/roman accidentally (I think) had the evdev driver instead of mouse in his earlier post.  Hopefully that helps.

---

### Post by pi/roman on 2010-02-19
[SIZE=1][COLOR=Black]T[/COLOR][/SIZE][SIZE=1][COLOR=#000080][COLOR=Black]his is his original fdi which was using the mouse driver and failed so I was trying to find something else that would work.[/COLOR]
[/COLOR][/SIZE][HTML]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_driver" type="string">mouse</merge>

    <!-- Logitech tweaks -->
    <match key="@input.originating_device:usb.045e" int="0x46d">
     <match key="@input.originating_device:usb.0059" int_outof="0xc50e;0xc518">
      <merge key="input.x11_options.RelHWHEELOptions" type="string">invert</merge>
     </match>
    </match>

   </match>
 </device>
</deviceinfo>[/HTML]

---

### Post by Ayuthia on 2010-02-19
> **pi/roman said:**
> [SIZE=1][COLOR=Black]T[/COLOR][/SIZE][SIZE=1][COLOR=#000080][COLOR=Black]his is his original fdi which was using the mouse driver and failed so I was trying to find something else that would work.[/COLOR]
[/COLOR][/SIZE][HTML]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_driver" type="string">mouse</merge>

    <!-- Logitech tweaks -->
    <match key="@input.originating_device:usb.045e" int="0x46d">
     <match key="@input.originating_device:usb.0059" int_outof="0xc50e;0xc518">
      <merge key="input.x11_options.RelHWHEELOptions" type="string">invert</merge>
     </match>
    </match>

   </match>
 </device>
</deviceinfo>[/HTML]

Sorry about that.  I missed that part (the removal of the </match>)from your earlier post.

---

### Post by pi/roman on 2010-02-19
No problem, you are much more knowledgeable than me and I've read some of your stuff on the wacom tablet even though I don't have one of them and it really is over my head so your advice is always welcome.  I was just trying to make the details clear in case it might help.

---

### Post by ronti69 on 2010-02-19
So I tried changing the fdi as Ayuthia suggested but it didn't work either. Funny thing, when I move the mouse, the pointer doesn't move, but the touchpad freezes for a few seconds

Even funnier, if I remove all of the fdi files and go back to the original mouse.fdi (which made the mouse work fine but killed the touchpad), I still cannot get the mouse to work!

Any other suggestions?

Thanks

---

### Post by ronti69 on 2010-02-19
Also, here are two more pieces of information. I don't really understand what they mean, so I don't know if they are useful;

[SIZE="2"]```
laptop:~$ xinput query-state "Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A"
2 classes :
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
	button[8]=up
	button[9]=up
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=640
	valuator[1]=360

```[/SIZE]

and 

[SIZE="2"]```
laptop:~$ xinput set-pointer "Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A"
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  12 (X_ChangePointerDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  14
  Current serial number in output stream:  14

```[/SIZE]

---

### Post by pi/roman on 2010-02-20
Have you tried these yet?
```
lshal -s | grep usb_device_45e_59_noserial | xargs -n1 lshal -u
xinput list | grep -i intellimouse | grep -o '"[^"]*"' | xargs xinput list-props
```

---

### Post by Kalam_ on 2010-03-09
Hi [ronti69]("http://ubuntuforums.org/member.php?u=598606")

Just curious if you got this issue resolved.  I to have a similar issue and have a TX2600 from HP as well.   

Regarding the touchpad I found I once disabled it because I unknowingly click on the small button above the touch pad (turning the blue icon orange) that disabled the touch pad.  Took me a while to finally notice what had happened, but click on the button again turned it back to icon back to blue and I had the touch pad working.

I'm going to follow the suggestions mentioned in the post as I can't get my mouse and touch pad working at the same time, though under Ubuntu 9.4 it seemed both worked by default.   Right now I resort to *sudo modprobe -r psmouse* to kill my touch pad which then allows me to use the mouse (after I re-plug it in).   *sudo modprobe psmouse* restores the touchpad and kills the mouse.    Hopefully I will be successful with one of the suggestions above.

~Kalam_

---

### Post by robomoon on 2010-05-01
This happened with a Medion notebook: Plugging in USB mouse, moving it, then the mousepointer accelerated too quickly and flickered while moving. Couldn't change this too fast pointer when changing the pointer speed. When removing the mouse and plugging it back into the USB, mouse didn't worked at all. Only the touchpad still worked.

Solution: adding the irqpoll command to the lines starting with the word kernel in the /boot/grub/menu.lst file. After rebooting that notebook, the mouse pointer from the external USB mouse worked OK. Next to this, irqpoll also helped to boot with an external DVD drive with Y cable.

---

