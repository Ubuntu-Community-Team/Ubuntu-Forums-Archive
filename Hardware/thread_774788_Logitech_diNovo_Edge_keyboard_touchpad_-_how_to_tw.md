---
title: "Logitech diNovo Edge keyboard touchpad - how to tweak settings?"
date: 2008-04-29
forum: Hardware
---

### Post by 23meg on 2008-04-29
I'd like to increase the sensitivity of and adjust the scrolling area width of the touchpad on the Logitech diNovo Edge keyboard, which works out of the box in Hardy, and since Hardy's xorg.conf has no entry for touchpads, I'm not sure which device it sends on and how to tweak it, and web searches didn't yield any results. Any help is appreciated.

---

### Post by 23meg on 2008-04-30
I [found out]("http://www.synaptics.com/press/pr_detail.cfm?id=113") that the touchpad on this device is a Synaptics one, so it should use the "synaptics" driver. But the following xorg.conf section hasn't helped:
```

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver    	"synaptics"
	Option 		"SendCoreEvents" "true"
	Option 		"Device" "/dev/psaux"
 	Option 		"Protocol" "auto-dev"
 	Option 		"SHMConfig" "true"
	Option	    	"MinSpeed" "0.7"
	Option	    	"MaxSpeed" "0.9"
      	Option      "AccelFactor" "0.0210"
EndSection
```

It almost certainly transmits on another device, and I need to find that out. gsynaptics is also not working, prompting that SHMConfig needs to be inserted into the xorg.conf even when it is (there are many other threads about this).

---

### Post by 23meg on 2008-04-30
Anyone?

---

### Post by 23meg on 2008-05-04
The device transmits on /dev/psaux and /dev/input/mouse2 (verified with *cat*). But I get the following in my Xorg.0.log with both devices:

> Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

---

### Post by 23meg on 2009-03-18
I've more or less solved this, as of Ubuntu 8.10.

```
xinput list
``` will list the input devices recognized by X. First, find the ID of your keyboard's touchpad; it will be the first entry listed as "Logitech Logitech BT Mini-Receiver" with the longer list of properties.

> "Logitech Logitech BT Mini-Receiver"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
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
"Logitech Logitech BT Mini-Receiver"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255


In the output above, it's 5. To see a list of tweakable properties, issue ```
xinput get-feedbacks 5
```

The output will be similar to this:

> KbdFeedbackClass id=0
	click is 0
	percent is 50
	pitch is 400
	duration is 100
	led_mask is 0
	global_auto_repeat is 1
PtrFeedbackClass id=0
	accelNum is 1
	accelDenom is 1
	threshold is 7


accelNum, accelDenom and threshold are the touchpad properties, which you can tweak in the following fashion:

```
  xinput set-ptr-feedback 5 7 5 2 
```

Here the first 5 is the device ID, and the rest correspond to threshold, accelNum and accelDenom respectively.

The device doesn't seem to expose a sensitivity property, but the control that can be achieved with the acceleration properties seems acceptable.

More information, including how to set these properties permanently, can be found at [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input).

---

