---
title: "one mouse button doesn't show up in xev"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by injoy on 2007-11-20
Hi, I'd earlier posted [here]("http://ubuntuforums.org/showthread.php?p=3803406") describing my mouse travails, and I think I've got all the bugs ALMOST fixed, except for one pesky little button.  (Started a new thread because a) I don't think this is necessarily a Logitech-specific issue anymore, certainly not a bluetooth issue, and b) no one was answering my first post. ;-))

Sidenotes: I'm a total newbie, and using gutsy.

I have an MX 1000, and the mouse button that doesn't work is the app switcher button on the left side.  (FYI, the cruise up/down buttons on top register as the same as the scrollwheel up/down, so those are technically "broken", too, but I don't care about those particularly.)

The relevant section of my xorg.conf is:```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "SendCoreEvents"
        Option          "Name"  "Logitech Bluetooth Mouse"
EndSection
```I've tried adding "Buttons" "12" and also "ButtonMapping" "1 2 3 8 9 10 11 12", but neither has any effect.  I've tried installing btnx, which won't recognize my mouse at all, and also lomoco, which is supposed to separate the cruise buttons from the scroll wheel, but it also doesn't recognize my mouse.

So... any ideas of how to get it to recognize a mouse button that won't show up in xev?  (NOTHING happens when I push the button, no output at all.)

Thanks!

**ETA:** I had to follow [the instructions here]("http://ubuntuforums.org/showthread.php?p=2334318#post2334318") to make it so I didn't have to replug my bluetooth dongle every time I rebooted, the consequence of which is that my mouse and keyboard now show up as separate entries in cat /proc/bus/input/devices, entries which are NOT usb (the phys line for the mouse reads only 00:07:61:47:D4:32).  I think that's why btnx and perhaps lomoco don't work.  The dongle is listed as USB, but the keyboard/mouse are not.

---

