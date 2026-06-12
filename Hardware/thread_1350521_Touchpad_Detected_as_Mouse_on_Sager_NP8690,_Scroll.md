---
title: "Touchpad Detected as Mouse on Sager NP8690, Scrolling Not Working"
date: 2009-12-09
forum: Hardware
---

### Post by Spoom on 2009-12-09
Hi folks,

Just got a new Sager NP8690 laptop and installed Ubuntu Karmic on it.  Upon installation, I was unable to use the scrolling on the touchpad at all.

The Preference -> Mouse dialog did not display a Touchpad tab.

**xinput list** says:
```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0

...

"ImExPS/2 Generic Explorer Mouse"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 13
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
I tried changing xorg.conf to use the synaptics driver, with the following changes to that section:

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "synaptics"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "on"
EndSection
```
Upon rebooting, the same issue occurred. I tried installing gsynaptics with **sudo apt-get install gsynaptics** but upon trying to run it directly after rebooting, I get:

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.
```
Same error if I access Preferences -> Touchpad.  At this point I'm lost as to how to proceed.  Any ideas?

---

### Post by msrinath80 on 2009-12-28
Hey, I plan to get this model too. Does everything else work OK with it? Webcam?? Suspend/Hibernate? Sound?

---

