---
title: "Thinkpad Trackpoint/USB Mouse behaviour"
date: 2008-08-25
forum: Hardware
---

### Post by robz0rz on 2008-08-25
Hello all

I own a Lenovo Thinkpad T61. I've been trying to get correct behaviour from the different mice. I managed to set up my touchpad the way I like it, but I'm having trouble setting up the trackpoint and the usb mouse correctly...

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"

    Option    "EmulateWheel"          "true"
    Option    "EmulateWheelButton"    "2"

EndSection
```

I've been following these guides on thinkwiki ([one]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#TrackPoint") and [two]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61#Trackpad_scrolling")) to get the scrolling working properly.

What I want is that the middle button on the laptop only ever scrolls, but performs a "middle-click" (for example to paste something) when used without moving the trackpoint. With the curreent configuration, this behaviour is archieved, but it messes with the usb mouse behaviour.

The usb mouse should just use the middle mouse button as a middle mouse button, without scrolling when I'm holding it while moving the mouse. I don't know how to properly edit the *xorg.conf* file so that it does this. How can I seperate the trackpoint from the usb mouse in the configuration file?

The method described in the first thinkwiki article I posted does not give good behaviour, none of the two posted configurations end up applying to my trackpoint, they are just ignored it seems. I'm guessing it's because of wrong identifiers or something, so I would be really glad if someone could tell me what the correct identifiers would be or where to find them (through some sort of command line command maybe?)


Sorry for the big post, I just wanted to be complete. I hope someone can help me

---

### Post by proxc on 2008-08-28
I don't understand this:
> 
What I want is that the middle button on the laptop only ever scrolls, but performs a "middle-click" (for example to paste something) when used without moving the trackpoint

Anyway, in order to specify only your trackpoint instead of all mice, you're going to need to create a udev rule based on /proc/bus/input/devices (take a look at [this]("http://www.nabble.com/synaptics-+-trackpoint-td3748313.html")).

I haven't personally done it, but I'd try Richard's instructions at the bottom of that page.

---

