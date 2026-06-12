---
title: "Mouse Button Mapping Issues"
date: 2013-07-11
forum: Hardware
---

### Post by Jackelope King on 2013-07-11
EDIT: Before I completely forget, I'm on 13.04 64bit.

I recently bought an [Anker High Precision Laser Gaming Mouse]("http://www.ianker.com/Anker-gaming-mouse-/product/98ANDS2368-BA"), but it has some very odd button-mapping on it, and was looking for some help with remapping it. Reading the manual that came with it, the company has mapped mouse buttons 4, 5 and 6 (along the thumb) as Ctrl, Shift and Alt, in that order. Buttons 7, 8 and 9 are for recording and replaying macros (which don't seem to work on Linux).

I'm trying to figure out how to remap the buttons on this mouse, but since 4, 5 and 6 default to keyboard commands, I'm having some difficulties. I started with [this guide](https://help.ubuntu.com/community/ManyButtonsMouseHowto) but was unable to get too far. The command imwheel -c gets a response of ```
INFO: imwheel started (pid=9971)
~$ Configuration terminated by signal 11
```

I ran xinput list, which makes it appear as though Ubuntu is recognizing the mouse as both a keyboard and a mouse (which I suppose makes sense given how its buttons are mapped by default by the manufacturer).```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; USB Laser Game Mouse                    	id=11	[slave  pointer  (2)]
&#9116;   &#8627; USB Laser Game Mouse                    	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; HID 0a5c:4502                           	id=8	[slave  keyboard (3)]
    &#8627; UVC Camera (046d:081b)                  	id=10	[slave  keyboard (3)]
    &#8627; USB Laser Game Mouse                    	id=12	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
```

Checking in xev gives me the following for buttons 4, 5 and 6:
```
KeyPress event, serial 41, synthetic NO, window 0x6000001,
    root 0x293, subw 0x6000002, time 4212806, (30,36), root:(544,88),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 41, synthetic NO, window 0x6000001,
    root 0x293, subw 0x6000002, time 4313925, (31,27), root:(545,79),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 42, synthetic NO, window 0x6000001,
    root 0x293, subw 0x6000002, time 4371805, (55,24), root:(569,76),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Buttons 7, 8 and 9 are stranger. 7 seems to give an output as Mouse 1 (which suggests the Macro it comes pre-programmed with is a left-click behavior). Button 8 (which according to the manual allows you to program a new macro) is not recognized as an input at all by xev. Button 9 is not recognized as input by xev, but it appears to match the listed behavior in the manual of adjusting scrolls-speed on the fly.

I'd like some help remapping the 4, 5 and 6 buttons if this is possible.

---

### Post by dcleal on 2013-07-11
That's a coincidence - I plugged one of these into my ubuntu box for the first time today as well ;)

Like you, I got nowhere with imwheel.

I installed btnx. This recognised the three side buttons and click on the scroll button, and let me assign arbitrary keystrokes to them, which is fine for my purposes. It doesn't recognise the middle buttons, which is a shame, but then neither does xev:

My xev investigation suggests that the button numbers are

left button: 1
scroll button (click): 2
right button: 3
scroll button (spin forward): 4
scroll button (spin back): 5 
middle button at the front: 1 (but one click generates two ButtonPress events)
middle button behind the scroll button: nothing - no response in xev.
middle button for mouse speed - no response in xev.

As you say, the three side buttons are mapped to key presses.

I imagine that the mouse speed button is entirely local to the mouse, which seems fair enough. It would be nice to get at the other middle buttons but I'm stumped as well at this stage.

- Dave

---

### Post by Jackelope King on 2013-07-11
> **dcleal said:**
> That's a coincidence - I plugged one of these into my ubuntu box for the first time today as well ;)
We must've seen the same sale haha.

Is there a working version of btnx for 13.04? I couldn't find it in the repositories.

---

### Post by dcleal on 2013-07-12
> **Jackelope King said:**
> Is there a working version of btnx for 13.04? I couldn't find it in the repositories.

Dunno - 12.10 here. I've mailed anker too, will report back if they come up with anything...

- Dave

---

### Post by Jackelope King on 2013-07-12
Alright, I got btnx and btnx-config sort of working on my system, and did the configuration with btnx-config, but I can't get it to apply. Instead I get the following error:
```
~$ btnx
 btnx: uinput modprobed successfully.
 btnx: Opening config file: /etc/btnx/btnx_config_Anker Default
 btnx: No configured mouse handler detected: No such file or directory
 btnx: Looped through all configurations. Stopping.
 btnx: Configuration file error.
```

---

### Post by dcleal on 2013-07-15
I ran it as sudo: there's a permissions issue in there somewhere, which I guess I'll try to fix properly if I stick with this arrangement.

- Dave

---

