---
title: "Synaptics touchpad tap/click style."
date: 2009-10-31
forum: Hardware
---

### Post by detroit/zero on 2009-10-31
In relation to another post I made [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8207099"), I've noticed with the upgrade to Karmic that the click style has changed somewhat for my Synaptics touchpad. I've discovered that the change is system-wide and not limited to Firefox.

Until now, a two-finger tap on my tab was equivalent to a middle-click. Now, a three-finger tap is the middle-click and a two-finger tap is a right click.

Does anyone know how to permanently change this behavior? The two-finger tap has been a default middle-click on a Synaptics touchpad for as long as I've been using laptops with them, and I'd rather stick with what I'm comfortable using. I thought I'd be able to open xorg.conf and change some settings, but much to my surprise, xorg.conf is apparently a thing of the past.

```
zero@zero-laptop:~$ xinput list
[other, seemingly unrelated hardware listed]
"SynPS/2 Synaptics TouchPad"    id=7    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
```

**EDIT: **I would also like to note that the correct device is identified by the system and it does respond to tapping and all inputs - just not the way it always has nor the way I want it to continue to. I'm not sure when or why this change was implemented, but I would like to return to old (familiar) behavior.

---

