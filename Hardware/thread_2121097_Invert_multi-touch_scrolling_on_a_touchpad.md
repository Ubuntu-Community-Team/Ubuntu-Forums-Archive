---
title: "Invert multi-touch scrolling on a touchpad"
date: 2013-02-28
forum: Hardware
---

### Post by sloe on 2013-02-28
Hi, I have an Asus G55VW laptop in which I've finally gotten all the hardware working 100%. There is one remaining issue that I'd like to fix, but since the search capability is currently offline I thought I would toss this out there if there is a quick answer.

The unit has an Elantech touchpad, X11 is using the synaptic driver to interface with it. The multi-touch capabilities work fine, but I would like to invert the X axis for scrolling - I want it to work like my iPad, instead of like the wheel on a scroll mouse. How do I do this, since that option doesn't appear in the Mouse and Touchpad settings GUI.

The relevant section in my xorg.conf:

```

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection


```

So, how do I accomplish this?

---

### Post by tgalati4 on 2013-02-28
This may work:

Option "InvertX" "on" 

or

Option "InvertX" "1"

From this:

[http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/evdev.4.html)

Here's another reference:

[http://fedoraproject.org/wiki/Input_device_configuration](http://fedoraproject.org/wiki/Input_device_configuration)

And from an old Karmic post:

xinput set-button-map "KYE  Traveler 350" 1 3 2 5 4 6 7 9 8
xinput set-int-prop  "KYE  Traveler 350" "Evdev Axis Inversion"  8 1 1

*evdev* is a generic input event driver.

---

### Post by sloe on 2013-03-03
I got it fixed by using Ubuntu Tweak. I found this tip after posting the question here on AskUbuntu, but I forgot to copy the link before I closed the browser, and I can't find it now for some odd reason.

---

