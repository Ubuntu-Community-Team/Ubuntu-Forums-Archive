---
title: "another hal/fdi question - flybook,penmountlpc"
date: 2008-12-14
forum: Hardware
---

### Post by w14 on 2008-12-14
Hi there,

For some reason I can't get the touchscreen to work on my Flybook after a fresh install of Intrepid. All worked fine in Hardy.

Background:

The touchscreen worked fine using the driver from the Plop Linux guys ([http://www.plop.at/en/touchscreen.html](http://www.plop.at/en/touchscreen.html)).

The old xorg config said:

Section "InputDevice"
    Identifier "touchscreen"
    Driver    "plpevtch"
    Option "Device" "/dev/input/event9"	
#    Option "Calibrate" 	# <-- uncomment this line to calibrate
    Option "MinX" "67"
    Option "MaxX" "1984"
    Option "MinY" "42"
    Option "MaxY" "1920"
EndSection

After installing Intrepid, I ran an lshal and got the following:

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'
  button.has_state = false  (bool)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PenmountLPC TouchScreen'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_5'  (string)
  input.device = '/dev/input/event9'  (string)
  input.product = 'PenmountLPC TouchScreen'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input9/event9'  (string)


So I created a file /etc/hal/fdi/policy/99-x11-touchscreen.fdi

<?xml version="1.0" encoding="utf-8"?>

<deviceinfo version="0.2">
    <device>
      <match key="info.capabilities" contains="input.mouse">
        <match key="info.product" contains="PenmountLPC">
            <merge key="input.x11_driver" type="string">plpevtch</merge>
            <merge key="input.x11_options.Calibrate" type="string">True</merge>
            <merge key="input.x11_options.MinX" type="integer">50</merge>
            <merge key="input.x11_options.MinX" type="integer">900</merge>
            <merge key="input.x11_options.MinX" type="integer">50</merge>
            <merge key="input.x11_options.MinX" type="integer">900</merge>
        </match>
      </match>
     </device>
</deviceinfo>

Unfortunately, restarting the hal doesn't make any difference and lshal reports the same driver.

Can anyone point me in the right direction?

---

### Post by w14 on 2008-12-16
Bump

---

