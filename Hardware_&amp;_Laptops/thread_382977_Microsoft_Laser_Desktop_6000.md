---
title: "Microsoft Laser Desktop 6000"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by hitch on 2007-03-12
I just purchased a laser dekstop 6000 and, aware that getting all the keys to work properly would be a challenge, set out to get it working as well as possible.
I have run into some strange results:

In order to get xev to register all the mouse button events, I need to use the evdev driver.
Unfortunately, as soon as I do that, I lose *all* the multimedia-type-keys on the keyboard.
That said, I don't get even half of those in the best of situations.
What can I do?  What am I doing wrong?
Or is it just something I have to live with?

---

### Post by hitch on 2007-03-13
I found this site:
[http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations)
which, while gentoo specific, offers an interesting suggestion - to configure the mouse as driver "mouse" and keyboard as "kbd" and to configure a *second* keyboard as evdev to get the extra buttons working.

this didn't actually make all the buttons work, as suggested, but it fixed the immediate problem of having to choose between side-scrolling on the mouse and multimedia buttons.
though the mutlimedia buttons are now unrecognized keycodes, but that's a problem i know how to deal with.

any suggestions for getting the rest of my stuff working?

here are the salient portions of my xorg.conf file:

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Keyboard2"
    Driver         "evdev"
    Option         "Device" "/dev/input/event2"
    Option         "Dev Phys" "usb-0000:00:1d.0-1/input1"
    Option         "Buttons" "64"
EndSection


Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Resolution" "1000"
    Option         "SampleRate" "1000Hz"
EndSection

---

