---
title: "ThinkPad Brightness OSD Update Problem w/ hacky solution"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by AnythingBut on 2007-07-22
I'm running Feisty on a ThinkPad T60.  The brightness buttons work properly except that the OSD doesn't report the changes.  The OSD always reports the highest brightness.  It seems that the problem is /proc/acpi/ibm/brightness always reports level 7.  A solution I found is to parse the brightness directly from /dev/nvram, much like the deprecated tpb package.

Edit the /usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux script at line 44 (I think) in the "ibm" section.  Replace
```
value="`cat $HAL_PROP_LINUX_ACPI_PATH | grep level: | awk '{print $2;}'`
```
with
```

value=`od -An --skip-bytes=94 --read-bytes=1 -t x2 /dev/nvram | sed 's/[[:space:]]*00.\([0-7]\)/\1/'`
```
 
This should grab the brightness value directly from nvram.  Here's what my entire hal-system-lcd-get-brightness-linux script looks like

```
#!/bin/sh
#
# Copyright (C) 2005 Richard Hughes <richard@hughsie.com>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.

if [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "pmu" ]; then
	value="`hal-system-power-pmu getlcd`"
	if [ $? -ne 0 ]; then
		echo "org.freedesktop.Hal.Device.LaptopPanel.NotSupported" >&2
		exit 1
	fi
	exit ${value}
fi

# Check for file existance and that it's readable
if [ ! -r $HAL_PROP_LINUX_ACPI_PATH ]; then
	echo "org.freedesktop.Hal.Device.LaptopPanel.NotSupported" >&2
	echo "$1 not readable!" >&2
	exit 1
fi

if [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "toshiba" ]; then
	# cat /proc/acpi/toshiba/lcd
	#  brightness:              5
	#  brightness_levels:       8
	value="`cat $HAL_PROP_LINUX_ACPI_PATH | grep brightness: | awk '{print $2;}'`"
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "asus" ]; then
	# cat /proc/acpi/asus/brn
	#  5
	value="`cat $HAL_PROP_LINUX_ACPI_PATH`"
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "panasonic" ]; then
	# cat /proc/acpi/pcc/brightness
	#  5
	value="`cat $HAL_PROP_LINUX_ACPI_PATH`"
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "ibm" ]; then
	# cat /proc/acpi/ibm/brightness
	#  level:          5
	#  commands:       up, down
	#  commands:       level <level> (<level> is 0-7)
	#value="`cat $HAL_PROP_LINUX_ACPI_PATH | grep level: | awk '{print $2;}'`" # Replaced 
	value=`od -An --skip-bytes=94 --read-bytes=1 -t x2 /dev/nvram | sed 's/[[:space:]]*00.\([0-7]\)/\1/'`
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "sony" ]; then
	# cat /proc/acpi/sony/brightness
	#  5
	value="`cat $HAL_PROP_LINUX_ACPI_PATH`"
	value=$(($value-1))
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "omnibook" ]; then
	# cat /proc/omnibook/lcd
	#  LCD brightness:  7
	value="`cat $HAL_PROP_LINUX_ACPI_PATH | awk '{print $3;}'`"
elif [ "$HAL_PROP_LAPTOP_PANEL_ACCESS_METHOD" = "sonypi" ]; then
	# spicctrl -B
	# 70
	# 0..255
	value="`/usr/bin/spicctrl -B`"
	RETVAL=$?
	if [ $RETVAL != 0 ]; then
		echo "org.freedesktop.Hal.Device.LaptopPanel.NotSupported" >&2
		exit 1;
	fi
	exit ${value}
else
	echo "org.freedesktop.Hal.Device.LaptopPanel.NotSupported" >&2
	echo "No ACPI method found" >&2
	exit 1
fi

exit ${value}
```

Is anyone else having this problem?  Does this solution work for your model?  Hopefully the kernel module is fixed in the next release so that /proc/acpi/ibm/brightness is correct.

---

### Post by Eddie Hung on 2007-07-23
I think this bug would suffer from the same problem as thinkpad-keys, described in the bug entry below:
[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/45404](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/45404)

I have a IBM X41 myself, and I noticed that doing a:
echo 0xffffffff | sudo tee /proc/acpi/ibm/hotkey
acpi_listen
makes all my Fn+* keys work - whereas before only Fn+BrightnessUp would work for example (Fn+BrightnessDown wouldn't).

Whilst this does not solve the problem completely (i.e. the /proc/acpi/ibm/brightness doesn't update) maybe the key could now run a script which does echo down into /proc/acpi/ibm/brightness, or something along them lines?

Eddie

---

### Post by AnythingBut on 2007-07-23
Hey Eddie,

I think that's a different though related bug.  The bug you mention seems to deal with the generation of acpi events.  The one I've addressed has to do with handling the event.

Interestingly, my T60 generates events like "video LCD0 00000086 00000000" when I hit the brightness buttons.  These are properly caught but, because of the problem in /proc/acpi/ibm/brightness, the resulting brightness is incorrect in the OSD.  This is the problem I managed to find a work around for.

My T60 does seem to have the hotkey problem that you've mentioned, but the video events seem to take care of things anyway (at least for brightness).  Though, thanks for the info!

---

### Post by Eddie Hung on 2007-07-25
Sorry if I wasn't too clear before: I was just trying to highlight the problems you might encounter when polling the NVRAM - which is what thinkpad-keys does.

The problem, as you may have mentioned, is inside the thinkpad-acpi module (was ibm-acpi), and does not work in the sense that it does not update /proc/acpi/ibm/brightness - despite it being able to detect when the brightness key has been adjusted.

A suggestion for a different workaround would be to detect and parse the key yourself - by echo-ing "up" or "down" into brightness in order to get it to sync up with the current brightness - this would be much better than polling the NVRAM.

If I get some time I'll try and conjure up a script which does this - but what do you think?

Thanks,

Eddie

---

### Post by AnythingBut on 2007-07-25
Sounds promising.  I didn't notice before that echo "down" > brightness changes the value in /proc/ in addition to the brightness.

I think one issue with your solution may be syncing up the initial brightness value with /proc/acpi/ibm/brightness.  Usually it reports the wrong value on startup.

By the way, my work around doesn't poll nvram.  It checks it only when the buttons are pushed.

---

### Post by Eddie Hung on 2007-07-25
Eek my mistake. I guess I saw NVRAM and instantly jumped to the conclusion that you're polling - rather than being called from inside a script that is triggered by interrupts.

Instead of writing a script, I'm going to try and compile the latest thinkpad-acpi sources and see if the problem has already been fixed, if not then I might have a pop myself then.

Eddie

---

### Post by AnythingBut on 2007-07-25
Let me know if it works!  I'd be interested.

---

