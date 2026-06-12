---
title: "KeySonic wireless keyboard, tap to click, not Synaptics"
date: 2008-11-19
forum: Hardware
---

### Post by voteforpedro on 2008-11-19
I've got a wireless KeySonic keyboard with integrated with touchpad. There is no way of disabling the tap-to-click feature because it is not installed or recognised as a Synaptics touchpad.

I am using Intrepid so it's not managed in xorg.conf. I tried copying a conf file into /etc/hal/fdi/policy/ to specify MaxTapTime = 0 and to enable SHMConfig, but the former did nothing and the latter made gsynaptics complain about SHMConfig not being enabled...

How on earth do I get rid of this annoying feature?! Here is the output from xinput list:

```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
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
"2.4G USB RF KeyBoard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"2.4G USB RF KeyBoard"	id=4	[XExtensionPointer]
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
"2.4G USB RF KeyBoard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

---

### Post by vintermann on 2010-04-24
Did you ever find an answer to this? I have a similar problem, with a non-synaptics touchpad on my laptop. I've figured out that it's registered as "ImExPS/2 Generic Explorer Mouse", and I've tried to use xinput to disable it thusly:

```
xinput set-int-prop "ImExPS/2 Generic Explorer Mouse" "Device Enabled" 8 0
```

after that it registers with property "Device Enabled" to 0 all right - but that appears to have no effect. Restarting HAL has no effect either. I'm on Karmic Koala.

---

### Post by samwho on 2010-07-20
I'd be really quite interested in an answer for this as well :)

It registers under lsusb:


```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 002: ID 05af:0630 Jing-Mold Enterprise Co., Ltd **
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:180c Ricoh Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Pretty sure it's the Jing-Mold one. And my xinput lisp output is:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Rx504B  Ver:3.03                        	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; **Macintosh mouse button emulation **       	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_1.3M                  	id=10	[slave  keyboard (3)]
    &#8627; Rx504B  Ver:3.03                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=16	[slave  keyboard (3)]

```

Pretty sure it's the one highlighted there... Could be wrong, but it seems like it's being recognised as a mouse as opposed to a touch pad. This is annoying because I'm always brushing past it and sending my cursor off somewhere random and it really disrupts my typing ^_^

---

