---
title: "How to create macro/hotkey for mouse clicks?"
date: 2008-10-20
forum: General Help
---

### Post by xubcel on 2008-10-20
Hello.  How can I use the keyboard to do mouse clicks (press left, release left, etc.).?

Thank you.

---

### Post by Rhubarb on 2008-10-20
This might just be possible using mouseemu.
mouseemu lets you bind the middle, scroll wheel, and right mouse buttons to keyboard buttons.  I'm not sure about left click though.
I'll get back to you if I discover how it's done.

---

### Post by Rhubarb on 2008-10-20
Ok, This mostly works with mouseemu, middle button and right mouse button can be bound to any button on your keyboard.
I won't detail how exactly this is done now, as I'm sleepy and might make a rather bad mistake.

After a little more research, it appears that xmodmap would be a better utility to bind mouse buttons to keyboard buttons.  I'll research more into this for you in ~ 12 hours from now.

Unless someone else can help you in the mean time, please be patient.

While I'm asleep, could you post why you want mouse buttons bound to keyboard buttons?  There may be a better solution for you.

---

### Post by Rhubarb on 2008-10-21
I've had a REALLY good look at xmodmap, xvkbd, mouseemu, and xbindkeys.
The closest I've gotten working is mouseemu, but that only works with binding middle and right mouse buttons to keyboard keys.

I've discovered lots of interesting stuff along the way, such as binding keyboard keys to mice, remapping keyboard keys to other keys, binding mouse buttons / keyboard keys to scripts, but nothing to do with binding mouse buttons to keyboard keys.

Just now I've discovered [evrouter]("http://www.bedroomlan.org/~alexios/coding_evrouter.html") it is supposed to let you bind anything to anything else.  It looks promising, if somewhat technical.

When I'm free I'll have a dig around in [evrouter]("http://www.bedroomlan.org/~alexios/coding_evrouter.html") to see what I can come up with.  If I can do it, I'll post back here with the instructions of how to do it for you.

---

### Post by xubcel on 2008-10-21
My touchpad's left button broke.

Transferring the function to another button should be simple, I thought, but I couldn't find much.

Thank you.

---

### Post by loomsen on 2008-10-21
I'm joining.

Actually I'm interest the most in assigning mouse-gestures like opera has for instance, which is hold right klick left/hold left klick right to move back/forward. 

Using this with Opera for years now, and it's just the most intuitive one can do imho.


@broken left touchpad button:

You may specify a whole lot of Options in your touchpad section in your xorg.conf.

It's located in /etc/X11/xorg.conf

But make sure you back it up. I'd suggest booting into single user mode, configuring your xorg.conf from command line, when done start up gnome with:
startx

If you like it how you configured it, log out again and do a usual boot into multi user mode! DON'T do too much as root.

```

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option  "LeftEdge"              "120"
    Option  "RightEdge"             "830"
    Option  "TopEdge"               "120"
    Option  "BottomEdge"            "650"
    Option  "FingerLow"             "14"
    Option  "FingerHigh"            "15"
    Option  "MaxTapTime"            "0"
    Option  "MaxTapMove"            "0"
    Option  "MaxDoubleTapTime"      "0"
    Option  "ClickTime"  "0"
    Option  "EmulateMidButtonTime"  "75"
    Option  "VertScrollDelta"       "10"
    Option  "HorizScrollDelta"      "0"
    Option  "MinSpeed"              "0.45"
    Option  "MaxSpeed"              "0.75"
    Option  "AccelFactor"           "0.020"
    Option  "EdgeMotionMinZ"    "30"
    Option  "EdgeMotionMaxZ"    "160"
    Option  "EdgeMotionMinSpeed"    "200"
    Option  "EdgeMotionMaxSpeed"    "200"
    Option  "EdgeMotionUseAlways"    "0"
    Option  "UpDownScrolling"       "1"
    Option "TouchpadOff" "0"
    Option "GuestMouseOff" "0"
    Option "LockedDrags" "0"
    Option "RTCornerButton" "2"
    Option "RBCornerButton" "3"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    Option "TapButton1" "0"
    Option "TapButton2" "0"
    Option "TapButton3" "0"
    Option  "CircularScrolling"     "0"
    Option  "CircScrollDelta"       "0.1"
    Option  "CircScrollTrigger"     "2"
    Option  "CircularPad"     "0"
    Option  "SHMConfig"  "true"
EndSection

```

Find your touchpad section, add all above options, and comment them out with prepending # to each line which shall be ignored.

Then just try different options and specify the ones you'd like. Most of them are self-explainatory, however, 
[HERES XORG-WIKI](http://www.x.org/wiki/)

---

### Post by Rhubarb on 2008-10-21
If you have a touchpad, then left clicking is quite easy to do.
Just tap the touch pad for left click, and double tap the touchpad for left double click.
No need to change your /etc/X11/xorg.conf at all.

I'll look in to evrouter later - it should be a nice challenge for me to do later today :)

---

### Post by loomsen on 2008-10-21
Well there's some truth with that :)

Anyway, looking forward to this too, now that compz provides a desktopmenu, this would offer a whole bunch of possibilities. At least I hope it will :)

---

### Post by xubcel on 2008-10-22
> **Rhubarb said:**
> If you have a touchpad, then left clicking is quite easy to do.
Just tap the touch pad for left click, and double tap the touchpad for left double click.
No need to change your /etc/X11/xorg.conf at all.


How does that drag and drop?

How does that highlight blocks of text?

Thank you.

---

### Post by Rhubarb on 2008-10-22
Drag and Drop:  tap twice,
The 1st tap is to select the icon.
Then hold your finger down on the 2nd tap, drag your finger along the trackpad, release your finger when you want to drop.

Highlighting blocks of text is similar:
Double tap to select a word, triple tap to select a line.
If you wish to specifically select a block of text, follow drag and drop above:
Tap twice, on the second tap hold down your finger, then drag your finger along to selectively highlight text.  Release your finger once finished.

It really is easy to do, but I will probably look into evrouter in an hour or two.
Mastering the touchpad is however more beneficial to know in the long run.

[http://youtube.com/watch?v=rF9sXAMLBW0](http://youtube.com/watch?v=rF9sXAMLBW0)
At the 15s mark you'll see how this is done, double tap and drag.
The video there isn't the best for instructional purposes, but you might get a brief idea of it.

---

### Post by xubcel on 2008-10-22
> **Rhubarb said:**
> Drag and Drop:  tap twice,
The 1st tap is to select the icon.
Then hold your finger down on the 2nd tap, drag your finger along the trackpad, release your finger when you want to drop.

Highlighting blocks of text is similar:

If you wish to specifically select a block of text, follow drag and drop above:
Tap twice, on the second tap hold down your finger, then drag your finger along to selectively highlight text.  Release your finger once finished.



These do not work.

Thank you.

---

### Post by xubcel on 2008-10-27
Has anyone had any luck yet?

Thank you.

---

### Post by loomsen on 2008-10-27
I stumbled upon easystroke recently. It does pretty much everything you want, and has a nice GUI for configuration as well.

```

sudo apt-get install easystroke
```

Enjoy

*edit*
Oh, and I'm using the compiz deskmenu in the meanwhile, which as well is highly (and pretty easily) configurable and adds a lot of usability.
[Here is a very nice howto set it up](http://ubuntuforums.org/showthread.php?t=875262)

---

### Post by Rhubarb on 2008-10-31
Sorry xubcel, I've lost interest in investigating for you there (too busy at the moment playing with Ubuntu 8.10).
But, as I said earlier, it is possible to tap on the touchpad to send a left-click.  This can be done for dragging, double clicking, and highlighting text easily.  There is no special configurations you need to do, it just works.  All you need to learn is to try it yourself (it's a bit difficult for me to explain - I might post a video of how to do it in future).

If you can't find easystroke in the repositories (I couldn't), you can grab it here:
[http://easystroke.wiki.sourceforge.net/](http://easystroke.wiki.sourceforge.net/)

---

