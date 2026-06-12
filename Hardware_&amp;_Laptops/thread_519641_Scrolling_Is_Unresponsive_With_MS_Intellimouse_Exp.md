---
title: "Scrolling Is Unresponsive With MS Intellimouse Explorer 4.0A"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by pete-woods on 2007-08-07
I've got an Intellimouse Explorer 4.0A connected via one of those little green USB->PS/2 adapter thingies. Now the obvious stuff like getting scrolling working and such like is fine. The problem is that if I scroll too fast, or not exactly the way it seems to want me to, then the result is either unresponsive scrolling or no scrolling at all. (also the middle button doesn't work, but I think that's just a limitation of the PS/2 adapter and functional scrolling is more important to me)

Additionally I can't change my hardware configuration (it's a work machine) and there's a KVM in the middle.

Anyone know how to fix this? I've only managed to find one person who had this problem, but he didn't get any replies.

---

### Post by pete-woods on 2007-08-07
I just tried the mouse on a Windows XP box. Seems to do the same thing on that. Hmm, maybe this scroll-whell needs special driver support...

---

### Post by david.hilton.p on 2008-01-21
I haven't seen your problem.  As you say, it is probably your mouse.

The xorg.conf needs to be manually configured for the intellimouse explorer 4.0a, in order to enable the side buttons.

I am posting this here because it popped up first when I searched...


This is what I have in my xorg.conf file.

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
#    Option         "Protocol" "evdev"
    Option         "Vendor" "Sysp"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection

```

---

