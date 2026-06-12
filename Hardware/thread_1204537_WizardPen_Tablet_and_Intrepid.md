---
title: "WizardPen Tablet and Intrepid"
date: 2009-07-04
forum: Hardware
---

### Post by guedesav on 2009-07-04
I've upgraded from Intrepid just now, and finally getting the final touches fixed up. Right now, I'm having some problem setting up my Tablet.

I've found [this nice tutorial](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html), but it has only helped me so much. I've tried using the source code and the pre-compiled driver and both are behaving the same. The tablet still does not respond properly, the mouse pointer does not move and I think there are still some properties to set up.

Here's some useful info on the subject:

HAL's FDI file
```

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
	<device>
	<!-- This MUST match with the name of your tablet -->
		<match key="info.product" contains="Genius MousePen 5x4 Tablet">
		    <merge key="input.x11_driver" type="string">wizardpen</merge>
		  	<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
			<merge key="input.x11_options.TopX" type="string">2399</merge>
			<merge key="input.x11_options.TopY" type="string">3696</merge>
			<merge key="input.x11_options.BottomX" type="string">30438</merge>
			<merge key="input.x11_options.BottomY" type="string">29425</merge>
			<merge key="input.x11_options.MaxX" type="string">30438</merge>
			<merge key="input.x11_options.MaxY" type="string">29425</merge>
	    </match>
	</device>
</deviceinfo>

```
lshal:
```

udi = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_03_0'  (string)
  info.product = 'Genius MousePen 5x4 Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial'  (string)
  info.vendor = 'UC-Logic Technology Corp.'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '30438'  (string)
  input.x11_options.BottomY = '29425'  (string)
  input.x11_options.MaxX = '30438'  (string)
  input.x11_options.MaxY = '29425'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '2399'  (string)
  input.x11_options.TopY = '3696'  (string)
  linux.device_file = '/dev/bus/usb/001/011'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 11  (0xb)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-1'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Genius MousePen 5x4 Tablet'  (string)
  usb_device.product_id = 4  (0x4)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'UC-Logic Technology Corp.'  (string)
  usb_device.vendor_id = 21827  (0x5543)  (int)
  usb_device.version = 1.1 (1.1) (double)
udi = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial_if0'  (string)
  info.product = 'UC-LOGIC Tablet WP5540U'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial_if0'  (string)
  input.product = 'UC-LOGIC Tablet WP5540U'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:03.0/usb1/1-1/1-1:1.0/input/input18/event11'  (string)

```

lsusb
```

Bus 001 Device 011: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet

```

xinput list:
```

"UC-LOGIC Tablet WP5540U"       id=7    [XExtensionPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1

```

Xorg's Log:
```
(WW) config/hal: no driver or path specified for /org/freedesktop/Hal/devices/usb_device_5543_4_noserial
(II) config/hal: Adding input device UC-LOGIC Tablet WP5540U
(**) UC-LOGIC Tablet WP5540U: always reports core events
(**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event11"
(II) UC-LOGIC Tablet WP5540U: Found x and y relative axes
(II) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
(II) UC-LOGIC Tablet WP5540U: Found absolute touchpad
(II) UC-LOGIC Tablet WP5540U: Found 7 mouse buttons
(II) UC-LOGIC Tablet WP5540U: Configuring as mouse
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: MOUSE)
(**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
(**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

Notice one strange thing: the name defined on the FDI file is "Genius MousePen 5x4 Tablet", even though the device name appears as "UC-LOGIC Tablet WP5540U" in /proc/bus/input/devices. If I set the name accordingle, Xorg gives me an error message instead:

```

(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(EE) module ABI major version (4) doesn't match the server's version (2)
(II) UnloadModule: "wizardpen"
(II) Unloading /usr/lib/xorg/modules/input//wizardpen_drv.so
(EE) Failed to load module "wizardpen" (module requirement mismatch, 0)
(EE) No input driver matching `wizardpen'
(EE) config/hal: NewInputDeviceRequest failed

```

---

### Post by Favux on 2009-07-05
Pretty sure the name is "UC-LOGIC Tablet WP5540U".  Something may be wrong with the driver.

Let's be optimistic and assume it just needs to be told usb is on.  And shoot for lucky and see if we can get it to identify itself as stylus to the relevant programs.

You can still use your Hardy xorg.conf setup in Intrepid.

---

### Post by guedesav on 2009-07-05
Using that FDI, I still get the same error:

```

(II) config/hal: Adding input device stylus
(II) LoadModule: "wizardpen"

(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(EE) module ABI major version (4) doesn't match the server's version (2)
(II) UnloadModule: "wizardpen"
(II) Unloading /usr/lib/xorg/modules/input//wizardpen_drv.so
(EE) Failed to load module "wizardpen" (module requirement mismatch, 0)
(EE) No input driver matching `wizardpen'
(EE) config/hal: NewInputDeviceRequest failed

```

and the tablet is not added to xinput. If I can see a pattern here, it's that "ABI class". Should I try to update XInput somehow?

---

### Post by guedesav on 2009-07-05
Here's what I got using xorg.conf instead:

```

(II) config/hal: Adding input device UC-LOGIC Tablet WP5540U
(**) UC-LOGIC Tablet WP5540U: always reports core events
(**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event11"
(II) UC-LOGIC Tablet WP5540U: Found x and y relative axes
(II) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
(II) UC-LOGIC Tablet WP5540U: Found absolute touchpad
(II) UC-LOGIC Tablet WP5540U: Found 7 mouse buttons
(II) UC-LOGIC Tablet WP5540U: Configuring as mouse
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: MOUSE)
(**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
(**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

This is the xorg.conf's added content:

```

Section "InputDevice"
	Identifier "UC-LOGIC Tablet WP5540U"
	Driver          "wizardpen"
	Option		"SendCoreEvents"	"true"
        Option          "TopX"          "2399"
        Option          "TopY"          "3696"
        Option          "BottomX"       "30438"
        Option          "BottomY"       "29425"
        Option          "MaxX"          "30438"
        Option          "MaxY"          "29425"
EndSection

```

But, oddly, the "wizardpen" driver itself is not loaded, it doesn't appear in lshal anymore... any guesses?

---

### Post by Favux on 2009-07-05
Hi guedesav,

I've seen the ABI error before.  It most likely means that your wizardpen driver is looking for a version of Xserver that is not the one on your Intrepid install.

So the wizardpen_drv.so is probably checking for the version.  And it's at "/usr/lib/xorg/modules/input/".  Apparently you can get around this by adding the following to xorg.conf:
```
Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection
```
If you're "confident" that the wizardpen_drv.so won't cause an error.

That should allow the driver to load and its configuration through the .fdi or xorg.conf.

This should tell you what Xserver you have:
```
dpkg -l xserver-xorg-core
```
1.5.2 in my case:
```
ii  xserver-xorg-c 2:1.5.2-2ubunt Xorg X server - core server
```

---

