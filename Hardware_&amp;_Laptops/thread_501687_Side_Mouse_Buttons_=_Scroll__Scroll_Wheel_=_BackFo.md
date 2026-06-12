---
title: "Side Mouse Buttons = Scroll | Scroll Wheel = Back/Forward"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by arpnuke on 2007-07-15
Hi, I'm using a Microsoft Habu mouse and want to get the side buttons to go forward and backward in firefox like windows does.  When configured automagically, I have the standard buttons and the scroll wheel working properly.

What I'm getting right now:  Side Forward button scrolls down and side back scrolls up.  The scroll wheel goes forward and backward in firefox.  Basically, the two functions are swapped from how I want them.

Relevant section of Xorg.conf
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option        "Resolution"        "800"
#    Option         "Name" "Tempest Habu Mouse"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
#    Option        "Protocol" "evdev"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "6 7"  #If changed to "4 5" the mouse wheel stops working and I have the same effect with the scroll wheel
EndSection

```

IMwheel is installed as many tutorials recommend.  I set startup.conf to let it start.  the following script starts when the gnome session comes up.
```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP
```

xev reveals that side forward is button 5 and backward is 4.  The scroll wheel registers as 8 for forward and 9 for backward.

/etc/X11/Xsession.d/63xmodmap 
```
killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "45"

```

.xsession in my home dir
```
exec xmodmap -e "pointer = 1 2 3 8 9 6 7 4 5" &
exec imwheel -k -b "89" &
exec $REALSTARTUP

```

---

### Post by daou on 2007-07-15
You could try using btnx-0.3.1 with btnx-config-0.1.7: [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

You might have to revert most of the changes you have made for it to work correctly.

---

