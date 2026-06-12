---
title: "Mouse: Horizontal movement twice as fast as vertical movement"
date: 2017-02-13
forum: Hardware
---

### Post by izznogooood on 2017-02-13
I recently bought a Lenovo Yoga 500 2in 1 laptop. One of the issues I'm having is the mouse moves very slow vertically.

I've tried solutions like adding:

```
Option "VertResolution" "xx"
Option "HorizResolution" "xx"
```

to /usr/share/X11/xorg.conf.d/50-synaptics.conf with different numbers but it makes no difference. It is constant.
I've also tried using libinput, this also has no effect.

Any suggestions would be greatly appreciated!

---

### Post by #&amp;thj^% on 2017-02-13
@izznogooood I came up with this...for different reasons...but should point you in good direction. My major problem (for my client) was too many intentional clicks from a clients Lenovo Yoga.
This is just an example of what worked for him:
```
# softlink this file into:
# /usr/share/X11/xorg.conf.d

# and prevent the settings app from overwriting our settings:
# gsettings set org.gnome.settings-daemon.plugins.mouse active false


Section "InputClass"
    Identifier "my touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"

    # three fingers for the middle button
    Option "TapButton3" "2"
    # drag lock
    Option "LockedDrags" "1"
    # accurate tap-to-click!
    Option "FingerLow" "50"
    Option "FingerHigh" "55"

    # prevents too many intentional clicks
    Option "PalmDetect" "0"

    [B]# "natural" vertical and horizontal scrolling
    Option "VertTwoFingerScroll" "1"
    Option "VertScrollDelta" "-75"
    Option "HorizTwoFingerScroll" "1"
    Option "HorizScrollDelta" "-75"[/B]

    Option "MinSpeed" "1"
    Option "MaxSpeed" "1"

    Option "AccelerationProfile" "2"
    Option "ConstantDeceleration" "4"
EndSection
```

I have bolded the text to pay note to.
Now this has been a year ago so my memory on this is a little fragmented...LOL;)
I wish you the best here.

---

### Post by izznogooood on 2017-02-14
Thank god for Zim then? :). Thank you, Ill give this a go when i get home.

---

