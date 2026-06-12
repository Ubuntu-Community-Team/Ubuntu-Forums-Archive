---
title: "xorg.conf, imwheel and Firefox"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by fizban9 on 2008-01-06
I'm trying to get my mouse mapping correct, specifically so that the 2 extra buttons work as back and forward in Firefox (in Nautilus also would be awesome).

Below is the mouse entry from my xorg.conf.  With it set up like this, my mouse scrool wheel controls back and forward and my extra buttons scroll.  I want the EXACT OPPOSITE of this.  I want my scroll wheel to scroll and my extra buttons to do left and right.  

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"       "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "ZAxisMapping"  "4 5"
EndSection


Also, if I change teh ZAxisMapping to "6 7" then my scroll wheel will start scrolling again but the extra buttons completely stop functioning.  

Here's some extra info too.  If I run imwheel -c I can find out the mapping of those four buttons (wheel up, wheel down and the 2 side buttons)

Wheel Up = Left (Button6)
Wheel Down = Right (Button7)
Extra Button on left = Up (Button4)
Extra Button on right = Down (Button5)

Thanks for any help.  I've been trying dozens of variations, each with it's own bizarre side effects.  I even tried to install bentx but it failed to install.

------------------------------

Took me over a dozen attempts, but heres the version that finally got it working, in case someone else wants to try it.

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"       "7"
        Option          "ButtonMapping" "1 2 3 4 5"
        Option          "ZAxisMapping"  "6 7"
EndSection


All I can say is, imwheel -c is your friend.

---

