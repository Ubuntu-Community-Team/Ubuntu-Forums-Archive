---
title: "Laptop Freezes unless USB Mouse is plugged in (8.10 and 8.04)"
date: 2009-04-02
forum: Hardware
---

### Post by Saitoh514 on 2009-04-02
I am a beginner when it comes to Linux, but at the suggestion of a friend I decided to give it a try. He told me to use Ubuntu and so here I am. This problem actually started even as I was installing the OS. The whole system would just lock up while I was setting up the install. I could still move the cursor, but everything else was non-responsive. Num lock, caps lock, ctrl+alt combos don't work, and I can't even eject the cd tray. I had to do a hard reboot to bring it back. Eventually I discovered that if I plugged in a usb mouse that I stole from my desktop everything was fine. 

So now that Ubuntu is installed, I still have the same problem. I have tried everything I could find on the forums and web. I found many similar problems, but no answers. Having a usb mouse plugged in all the time kinda defeats the purpose of a laptop, plus I really want to figure this out. I am only a beginner at Linux so I definitely need some help diagnosing and solving this. Here is some general info about my system and what I have tried already:

Acer TravelMate 8006lmi
2.0 ghz Centrino
1 gb ram
ATI Mobility Radeon 9700 128 mb
SynPS/2 Synaptics TouchPad

/ -10 gb primary partition
/home -20 gb logical partition
/swap - 2gb logical partition

xinput list
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
"<default pointer>"	id=2	[XExtensionPointer]
	Num_buttons is 9
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
"<default keyboard>"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Microsoft Microsoft Wireless Optical Mouse? 1.00"	id=7	[XExtensionPointer]
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
"Video Bus"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

Some key things I found in Xorg.0.log
```
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "<default pointer>"
(==) |-->Input Device "<default keyboard>"
(==) No Layout section. Using the default mouse configuration.
(==) No Layout section. Using the default keyboard configuration.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(skip many pages of Radeon stuff)

(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) <default keyboard>: always reports core events
(**) Option "Protocol" "standard"
(**) <default keyboard>: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) <default keyboard>: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) <default keyboard>: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) <default keyboard>: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) <default keyboard>: CustomKeycodes disabled
(II) evaluating device (<default pointer>)
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) evaluating device (<default keyboard>)
(II) XINPUT: Adding extended input device "<default keyboard>" (type: KEYBOARD)
(II) <default pointer>: Setting mouse protocol to "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event8"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: Device: "/dev/input/event2"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"

```

Here are some of the symptoms I experience:
Stock install no external equipment - freeze within seconds of booting X whether I log in or not
When unable to login the blinking bar disappears. The mouse still moves and the cursor changes when I mouse over the text field, but over time the mouse cursor becomes jerky.
When I am able to login, the system will usually freeze before the menu bars load, leaving just a movable wait cursor.
Should the menu load, the freeze will come soon after and the cursor get stuck as whatever it happens to be at the moment (text input, window stretch, wait icon, etc)
In all cases of a freeze the cursor still moves, but everything else is frozen including ctrl+alt combos, numlock and capslock button/lights, eject cd tray button. The HD activity light also stops moments after a freeze.
When I unplug the usb mouse, the system freezes again after unloading the "evdev" module

Solutions Tried:
Plug in external usb mouse - system works 100% but this a temporary solution at best.
Modified Xorg.conf adding sections for my mouse and keyboard and making them core devices (I don't know if I did this correctly) - gets me to the desktop, but freezes soon after
Modified Xorg.conf adding:

Section "Server Flags"
	Option 		"AllowEmptyInput" "off"
EndSection

Section "Module"
	Load 		"evdev"
EndSection
result was the same as other xorg.conf modification

Tried using different usb device, but was unable to login. It was a usb flash drive and the light got stuck on while system froze.
Tried Ubuntu 8.04 Live CD, but had the same problems.
Checked ordering of gdm load and hal
Tried sudo dpkg-reconfigure -phigh xserver-xorg - nothing updated, no changes, still freezes
Tried some other command line that I cannot remember. I had something input-all in it. All i remember is it broke my wireless and i had to reinstall.

Most of the info was gathered with the usb mouse plugged in since i don't really know how to get to it otherwise. I am still digging around for answers so any help would be appreciated. If you need more info just let me know how and what and i will post it asap. Thanks.

P.S. Sorry for the enormous post, I just wanted to be detailed and thorough

---

### Post by Moriddin on 2009-05-04
I have almost the same laptop and have exactly the same problems (acer travelmate 8005LMi)

I tried several suggestions that I found by searching for the problem but none worked.The ones I found were :

- adding i8042.nomux=1 and/or i8042.reset=1to the statup line in grub
- Define input devices in xorg.conf

**When Ubuntu starts up i have:**
- autologin
- passwork dialog for keyring


My observation of the problem(s):

**When I don't have a mouse plugged in:**

Ubuntu loads normally. When gnome starts everything works for about 1 or 2 seconds. After this everything freezes except for the mouse pointer. If i move the pointer over the password dialog it doesn't even change to the edit cursor.
The only way to continue is to turn off the computer while holding the on/off button for several seconds.

**When a (usb) mouse is plugged in:**
 - Everything works perfect. 
 - When I remove the mouse gnome freezes again.



I really like ubuntu but its just very annoying to have mouse attached all the time. 

Can anyone help me/us? If not can anyone point me to the best place to make a bug report. 
I'm new to ubuntu but I have some experience with linux servers.

btw I'm using ubuntu 9.04 so the error is still there

---

### Post by nixusr on 2009-05-06
I have the same model of laptop and were experiencing the same problems.

Acer TravelMate 8006LMi
2.0 ghz Centrino
1 gb ram
ATI Mobility Radeon 9700 128 mb

I have tried Ubuntu 8.04, 8.10 and 9.04 alpha, all with the same result as you are describing. In lack of finding a solution I waited for the final release of 9.04. 

Today I installed Xubuntu 9.04 with latest updates and still experienced the same problem, but this time I did find some more information. 

Have a look at this thread 
[http://ubuntuforums.org/archive/index.php/t-779231.html](http://ubuntuforums.org/archive/index.php/t-779231.html) 
 
The suggestion from **porksome** is to add some kernel boot options 
highres=off nohz=off irqpoll 

It worked for me, finally! 

Good luck with yours!

---

### Post by Moriddin on 2009-05-07
Great this was exactly what I needed !

I tried a couple of kernel options but didn't try these.

Thank you very much.

---

