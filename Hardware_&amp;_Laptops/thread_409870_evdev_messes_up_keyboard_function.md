---
title: "evdev messes up keyboard function"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by tamagotono on 2007-04-15
I am trying to configure a Logitech VX Revolution mouse and the extra buttons.  I found that this can be done by using the evdev driver in xorg.conf.

I got it working great.  All buttons work and I love it.  However,  when I use the evdev driver my keyboard stops working correctly.  My arrow keys do not work as normal, when I press the UP arrow it calls the screenshot app and the PGUP key acts as a backslash.

The keyboard works fine if I use the standard "mouse" driver instead of "evdev" but then I loose the functionality of the extra keys on the mouse.

I have seen a few other reports of the same thing but nothing on how to resolve the problem.  I am running fiesty with full updates on a Compaq V3000 laptop.  Does anyone else use the evdev driver on this model laptop and have it working?

Any help would be appreciated

---

### Post by tamagotono on 2007-04-17
OK, I've found that when using the "evdev" driver instead of the "kbrd" driver the key codes are different for the keys "home" "pg up" "pg dn" "end" "delete" and the arrow keys.  anyone have any idea where the settings for this keyboard are coming from so I can change it?  I am not trying to use evdev as the keyboard driver, only for the mouse.

---

### Post by stafio on 2007-05-04
Can you post your keyboard configuration from /etc/X11/xorg.conf?

If your not familiar, it should look something like this:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	...
	...
	...
EndSection

Note, it may not be called "Generic Keyboard", but it should have the word keyboard in there.

---

### Post by tamagotono on 2007-05-07
Thank you for your reply.  I was away from my computer for a few days but should be able to reply quicker now.

Here is the information you requested...

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection


Hope it helps,

---

### Post by stafio on 2007-05-09
Try changing your keyboard set up to match the following:

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver         "evdev"
    Option         "Device" "/dev/input/event0"    ### event device according to /proc/bus/input/devices
    Option         "XkbModel" "evdev"
    Option         "XkbLayout" "us"
EndSection

For the Option "Device" line, open up a terminal and enter: ```
cat /proc/bus/input/devices
```
Here's the output for my keyboard:
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

```

You need the event# from the H: Handlers line for your xorg.conf file. 

Just out of curiosity, is there only one keyboard InputDevice entry in your xorg.conf? If there is more than one, that could also potentially be causing the problem.

---

### Post by Eil on 2007-08-11
I'm having the same problem here on two different machines, one running Ubuntu Feisty and one running Gentoo. When the evdev driver is loaded in X, the arrow keys and the Insert, Del, Home, End, Page Up, Page Down block stops working properly. It's like the wrong keycodes are being sent. Note that stafio's suggestion does not help because these are PS/2 keyboards. I don't know why the evdev driver should have any effect on a PS/2 keyboard, but it does. Here are the relevant sections from my xorg.conf:

```
Section "InputDevice"
 Identifier  "Keyboard0"
 Driver      "kbd"
 Option     "XkbModel" "pc104"
 Option     "XkbLayout" "us"
 Option      "1 2 3"
 Option      "AutoRepeat" "250 30"
EndSection
```

```
Section "InputDevice"
        Identifier "MightyMouse"
        Driver "evdev"
        Option "SendCoreEvents"
        Option "HWHEELRelativeAxisButtons" "7 6"
        Option "Buttons" "8"
EndSection
```

---

### Post by Eil on 2007-08-11
Alrighty, I got this figured out. After reading the evdev man page, I found that the evdev driver is a general-purpose input driver, not just for certain types of keyboards and mice. I still don't know why on earth the evdev driver is grabbing the keyboard when I only wanted to use it for the mouse, but the following snippet seems to work for the keyboard definition in xorg.conf:

```

Section "InputDevice"
 Identifier "Keyboard0"
 Driver "evdev"
 Option "evBits" "+1"
 Option "keyBits" "~1-255 ~352-511"
 Option "Pass" "3"
 Option "Name" "AT Translated Set 2 keyboard"
 Option     "XkbModel" "evdev"
 Option     "XkbLayout" "us"
 Option      "1 2 3"
 Option      "AutoRepeat" "250 30"
EndSection

```

---

