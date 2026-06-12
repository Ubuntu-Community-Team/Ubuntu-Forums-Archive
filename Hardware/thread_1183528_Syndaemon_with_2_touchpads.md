---
title: "Syndaemon with 2 touchpads"
date: 2009-06-10
forum: Hardware
---

### Post by FokkerCharlie on 2009-06-10
Hello!

I have a continuing issue with syndaemon on my laptop- the program seems to run fine, but targets the wrong touchpad - here's xinput list:

```
$ xinput list
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
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=3	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=4	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1

```

You see both touchpads, ids 4 and 5... well, 4 is not actually a conventional touchpad, but 4 touch-sensitive media keys.  I have successfully mapped these keys to mouse buttons, but that's another story.

When syndaemon runs, and I use the keyboard, the media keys are temporarily disabled, rather than the main touchpad.  That's not what we want!  Is there a way of getting syndaemon to target a particular device, or even both of them?

Using Ubuntu Jaunty 64.

Thanks in advance
Charlie

---

### Post by FokkerCharlie on 2009-06-11
Bump!

Any ideas?  Come on!

Charlie

---

### Post by FokkerCharlie on 2009-06-19
Bump again!

I think that this may become an even more pressing issue under Ubuntu 9.10 with changes to xserver-xorg.  My understanding is that the default setup for the touchpad (which I and other 5920 users, and maybe others are forced to use) will be change, and no longer include tapping.

That, I'm afraid, will render my touchpad barely useable, and have a significant impact on the efficacy of Ubuntu.... boo!

Please please please please someone give us something to work with!

Charlie

---

### Post by mohr tutchy on 2009-06-29
You need to write a /etc/hal/fdi/policy/touchpad.fdi file like this.
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input">
        <merge key="input.x11_options.SHMConfig" type="string">True</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
    </match>
  </device>
</deviceinfo>
```

The most important part is line 4. You can find the right info.udi string with
```
hal-device
```

I'm here if you have any problem :)

Sorry for bad english :s

---

### Post by FokkerCharlie on 2009-06-30
Ah-ha, thanks Mohr.

I will have a tinker to see if I can get it working with my setup.

I'll let you know the outcome!

Charlie

---

### Post by FokkerCharlie on 2009-06-30
Hooooray!

It works with the text exactly as you have it above on my machine.  I also needed to remove another fdi file that I had created to enable SHMconfig.

Nice one, many thanks.

Charlie

---

