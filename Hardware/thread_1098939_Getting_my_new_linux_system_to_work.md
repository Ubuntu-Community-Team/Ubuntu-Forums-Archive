---
title: "Getting my new linux system to work"
date: 2009-03-17
forum: Hardware
---

### Post by kovariadam on 2009-03-17
Hello,
i have newly installed linux, but i have few questions.

I need to get my Razer deathadder to work probably with HAL? and also my Microsoft Natural Ergonomic Keyboard 4000.

I have put these lines to my xorg.conf:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Deathadder"
    Option         "Vendor" "Razer"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Resolution" "1800"
    Option         "SampleRate" "1000Hz"
EndSection

```

but my left buttons still don't work. I guess it's because system uses HAL configuration instead of xorg. What to do?

To my keyboard: I have my .Xmodmap file from old installation but when i apply it on this system, keyboard is totaly crazy. I mean arrows call weird programs, so it's basicly mess. I guess it's because of wrong type of keyboard recognized by HAL again?

Please, I need some basic information, i'm willing to write FDI files for HAL if that's what i need. I just don't know where is the problem. Is it Xorg or HAL or something else?

My distribution is Fedora 10 x86_64 and i use KDE 4.2.1.

Thanks for help

---

