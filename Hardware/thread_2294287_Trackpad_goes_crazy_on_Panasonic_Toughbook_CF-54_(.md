---
title: "Trackpad goes crazy on Panasonic Toughbook CF-54 (14.04 &amp; 15.04)"
date: 2015-09-10
forum: Hardware
---

### Post by albert_3 on 2015-09-10
Hi,

My trackpad seems to go crazy on Ubuntu. When touched it randomly moves the cursor (very fast) and presses various buttons. While debugging this behavior I noticed that there are in fact two devices that are detected by the system:

&#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#8627; PS/2 Generic Mouse                          id=16    [slave  pointer  (2)]

In fact the "PS/2 Generic Mouse" appears only after I touch the trackpad (tested multiple times). It seems that all trackpad events are handled by the "PS/2 Generic Mouse" and disabling it also disables the trackpad while changing "SynPS/2 Synaptics TouchPad" has no effect.

Any ideas?

[B]This might be useful: (reset mouse)

[/B][  1628.889] (II) config/udev: removing device PS/2 Generic Mouse
[  1628.900] (II) evdev: PS/2 Generic Mouse: Close
[  1628.900] (II) UnloadModule: "evdev"
(EE) SynPS/2 Synaptics TouchPad: Read error 19
[  1628.976] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
[  1628.988] (II) UnloadModule: "synaptics"
[  1633.810] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  1633.810] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  1633.836] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[  1633.836] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  1633.836] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  1633.836] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  1633.836] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  1633.836] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  1633.836] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  1633.836] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1633.836] (**) Option "Device" "/dev/input/event7"
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1336 - 5712 (res 53)
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1198 - 4656 (res 82)
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  1633.844] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1633.844] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1633.856] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input509/event7"
[  1633.856] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[  1633.856] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  1633.856] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[  1633.856] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[  1633.856] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  1633.856] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  1633.856] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  1633.856] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  1633.856] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

[B]After first trackpad touch:
[/B]
[  1658.900] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse3)
[  1658.900] (II) No input driver specified, ignoring this device.
[  1658.900] (II) This device may have been added with another device file.
[  1658.916] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event16)
[  1658.916] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[  1658.916] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[  1658.916] (**) PS/2 Generic Mouse: always reports core events
[  1658.916] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event16"
[  1658.916] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[  1658.916] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[  1658.916] (--) evdev: PS/2 Generic Mouse: Found relative axes
[  1658.916] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[  1658.916] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[  1658.916] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[  1658.916] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1658.916] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input569/event16"
[  1658.916] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 16)
[  1658.916] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[  1658.917] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[  1658.917] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[  1658.917] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[  1658.917] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4

---

### Post by tgalati4 on 2015-09-10
I've seen this behavior on a damaged or wet trackpad.  How beat up is the Toughbook?  Perhaps open it up and disconnect the ribbon cable and use an external mouse.  See if the computer input is stable after that.

Try running some tape around the edges to pick up dirt.  All it takes is some conductive dirt in the edges to really mess up a trackpad.

---

### Post by albert_3 on 2015-09-11
The Toughbook is new and trackpad works fine under Windows.

---

### Post by tgalati4 on 2015-09-11
This post explains the relationship between *evdev* and the Synaptic touchpad module.  I appears that you have multiple processes that want to grab the touchpad and thus it is getting reset constantly.  Could be a kernel or xorg bug.

[http://www.linuxquestions.org/questions/slackware-14/should-i-be-using-evdev-or-synaptics-for-my-touchpad-4175452406/](http://www.linuxquestions.org/questions/slackware-14/should-i-be-using-evdev-or-synaptics-for-my-touchpad-4175452406/)

---

### Post by albert_3 on 2015-09-12
I'll have a look. But it seems it's just recognized as two separate devices on serio1 and serio2 and there are not resets other than those I trigger for debug purposes.

---

### Post by tgalati4 on 2015-09-12
Post the output of:

```
ls /dev/input
xinput list
```

Mine looks like:

> 
tgalati4@Mint17 /dev/input $ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Acer CrystalEye webcam                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
tgalati4@Mint17 /dev/input $ ls
by-id  by-path  event0  event1  event10  event2  event3  event4  event5  event6  event7  event8  event9  js0  mice  mouse0


The fact that you have 16 events defined seems strange--perhaps you have dual entries for your trackpad.

---

### Post by albert_3 on 2015-09-15
It sure seems I have dual entries for the trackpad (as I mentioned the second entry appears on first trackpad interaction). I'll post the full result when I'm next to the computer tomorrow but the dual entry I see as I mentioned in the original post is:

> 
&#8627; SynPS/2 Synaptics TouchPad id=14 [slave pointer (2)]
&#8627; PS/2 Generic Mouse id=16 [slave pointer (2)]


---

### Post by tgalati4 on 2015-09-15
The jerky behavior could be Xorg is rapidly switching between them and with slightly different settings, you will get strange input behavior.  Many input devices are virtual--like an external keyboard that is plugged into a laptop.  Xorg will take input from either keyboard, but the second keyboard is defined as an input and is quiet until a real keyboard is plugged in.

In your case, you have 1 trackpad, but two sets of inputs defined, and both are active.  If you have an external USB trackpad or Wacom tablet, plug that in and see what happens.  It's possible the second device will then pull focus and then your internal trackpad will work normally.  Also try with an external mouse.

Either way, it appears to be a bug in Xorg or evdev or something else.

---

### Post by albert_3 on 2015-09-16
It works fine with an external mouse (Microsoft).

Here is the  output. The Wacom device is the touchscreen:

Before first touch
> 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=10    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID Finger touch                      id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Panasonic Laptop Support                    id=15    [slave  keyboard (3)]

by-id    event0  event10  event12  event14  event2  event4  event6  event9  mice    mouse2
by-path  event1  event11  event13  event15  event3  event5  event8  js0     mouse0


After first touch:

> 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=10    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID Finger touch                      id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Panasonic Laptop Support                    id=15    [slave  keyboard (3)]

by-id    event0  event10  event12  event14  event2  event4  event6  event9  mice    mouse2
by-path  event1  event11  event13  event15  event3  event5  event8  js0     mouse0




---

### Post by tgalati4 on 2015-09-17
Perhaps the touch screen is acting up and interfering with the touchpad.  Is there a way to turn off the touch screen in BIOS?

---

### Post by albert_3 on 2015-09-20
nope :(

---

### Post by tgalati4 on 2015-09-20
Some reading:  [https://digimend.github.io/support/howto/drivers/evdev/](https://digimend.github.io/support/howto/drivers/evdev/)

If you can get some control over your touchscreen, then I think you can work the touchpad issue.

---

