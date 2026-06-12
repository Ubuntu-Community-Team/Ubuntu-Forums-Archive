---
title: "Emulate Mouse Scroll Wheel on Keyboard?"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by Jamie Jackson on 2007-07-03
The mouse wheel is pretty darn convenient. Is there a way to emulate its behaviors when I'm on my mouse-less laptop?

Thanks,
Jamie

---

### Post by Megatog615 on 2007-07-03
Add these under Section "InputDevice"(for your mouse)
```
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
```
These options should be enabled by default...

---

### Post by Jamie Jackson on 2007-07-03
Doesn't this just enable a physical, external mouse's scroll wheel to work?

If so, that doesn't quite answer my question (I don't use an external mouse, by choice.)

If not, how do I then emulate the scroll wheel from my keyboard (or pointer stick, or touch pad, etc.) after having verified that I've got these settings?

Thanks,
Jamie

---

### Post by wrongo on 2007-07-04
Yes. Please, help. Scrolling would be great! Thanks!

---

### Post by kerry_s on 2007-07-04
i don't understand.
do you not have a touchpad/pointer at all?

there is a keyboard mouse control, that actually controls the mouse, but it's a little tricky on a laptop.

hold shift+ctrl and press the numlk, you might hear a beep, mine doesn't beep on this laptop, but did when use a regular keyboard, that activates keyboard mouse control. on my laptop the number key's are accessed by holding the fn key.

# 7, 8 ,9 are the up directions
# 4, 6 are left and right
# 1, 2, 3 are the down directions

/ is the left mouse key
* is the middle mouse key
- is the right mouse key

#5 is the click

you select which mouse key you want and then press#5 to use it.
example: i move the mouse where i want it and i want to middle click, so i press the * key and 5 to click.

hope that helps


now if that's not what you meant and you just want to scroll up and down, left and right, you can use the arrow keys, enter is the same as left click, the menu key(right side next to alt) is the right click, ctrl+enter is like a middle click

---

### Post by Jamie Jackson on 2007-07-04
Thanks, kerry_s

That's getting closer, and it helps me to refine my request.

I guess what I like about the scroll wheel on an external mouse is the variable speed control, and the fact that I don't have to move my hand to use it. (Arrow keys are good, but the scroll speed is constant and I have to move my hand pretty far.)

Here's the type of thing I wish I had:

A friend of mine has a keyboard on which there is a dedicated part of the touchpad (the right side) that emulates a scroll wheel. It's a hardware feature of that specific laptop.

It would be nice to be able to, say,  dedicate a part of my conventional touchpad to emulate the scroll wheel. (Or all of it, because I only really use the pointer stick.)

Or, it would be nice to, say, hit the function key to toggle the pointer stick's mode from pointer to scroll wheel emulation.

I realize I'm being picky, and I won't push the issue much further, but I'm just wondering if there's something out there already that does this sort of thing.

Thanks,
Jamie

---

### Post by Ayuthia on 2007-07-04
If you have a synaptics touchpad entry in your /etc/X11/xorg.conf, you might be able to add the feature there by adding this as another option:
Option        "VertEdgeScroll" "true"

That might give you the ability to use the right side of your touchpad as a scrolling device.  If you do go this option, you will have to restart your session to get the configurations to work.  I have also heard of installing gsynaptics, but I am not for sure if that will allow you to add that option or if it just allows you to do some typical mouse configurations.  If that works, there are other options that you can try by opening up a terminal and type:
man synaptics

It will give you a list of options that you can add to your xorg.conf file.

---

### Post by kerry_s on 2007-07-04
Okay i think i understand? your saying you have a touch pad but it doesn't have the scroll feature built in, but you want that feature.

like "Ayuthia" said you can try and put it to see if you can get it.

alt+f2 type> gksu gedit /etc/X11/xorg.conf
(be very careful in there, you mess up those settings and the gui won't work)

```
Section "InputDevice"
   Driver "synaptics"
   Identifier "TouchPad"
   Option "Device" "/dev/input/mouse0"
   Option "Protocol" "event"
   Option "LeftEdge" "130"
   Option "RightEdge" "840"
   Option "TopEdge" "130"
   Option "BottomEdge" "640"
   Option "FingerLow" "7"
   Option "FingerHigh" "8"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "110"
   Option "EmulateMidButtonTime" "75"
   Option "VertScrollDelta" "20"
   Option "HorizScrollDelta" "20"
   Option "MinSpeed" "0.60"
   Option "MaxSpeed" "1.10"
   Option "AccelFactor" "0.030"
   Option "EdgeMotionMinSpeed" "200"
   Option "EdgeMotionMaxSpeed" "200"
   Option "UpDownScrolling" "1"
   Option "CircularScrolling" "1"
   Option "CircScrollDelta" "0.1"
   Option "CircScrollTrigger" "2"
   Option "SHMConfig" "on"
   Option "Emulate3Buttons" "on"
 EndSection
```

After you add those settings to your synaptics section, logout and press ctrl+alt+backspace to restart X
if you want to try the gui> [http://linuxinside.blogspot.com/2007/06/touchpad-configure-it.html](http://linuxinside.blogspot.com/2007/06/touchpad-configure-it.html)

---

### Post by Jamie Jackson on 2007-07-06
This is a great solution. I ended up using the gsynaptics GUI.

Notes to self:

#enable scrolling (emulating mouse wheel) from the touchpad
sudo apt-get install gsynaptics
gksudo /etc/X11/xorg.conf
# add... 
# Option "SHMConfig" "true"
# ... to InputDevice "Synaptics Touchpad" section
# reboot
# System > Preferences > Touchpad > Scrolling > (Check) Enable vertical scrolling

After doing this, if I use the right edge of the touchpad, it controls the scrolling.

Thanks everyone, :popcorn:
Jamie

---

