---
title: "touchpad taps"
date: 2008-05-22
forum: Hardware
---

### Post by raequin on 2008-05-22
Hi, all. I have been trying since installation of Hardy to get my touchpad working well when I type. I have edited xorg.conf, as shown below. Syndaemon has no effect when I run it. Also, System->Preferences->Mouse changes nothing, even when I uncheck the box "enable touchpad."

There are only two things that I can do to affect the touchpad, use Fn+F7 that is the touchpad on / off button that came with the laptop (an Acer), or use Mousetweaks pointer capture on the panel.

I would like to be able to either turn off the touchpad with either keyboard shortctus or by terminal command (which maybe I could bind to a keyboard shortcut), or get syndaemon working so that I can type without worrying about the touchpad.

Here is a part of xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "on"
# Option "MaxTapTime" "0"
EndSection

"MaxTapTime" did nothing either, so I commented it out. Nothing I do in gsynaptics has any effect.

I tried installing gsynaptic, and received the following message:

sudo apt-get install gsynaptic
...
Reading state information... Done
Note, selecting synaptic instead of gsynaptic
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also tried the following line instead of what is posted above, in xorg.conf:
Option "SHMConfig" "true"

---

