---
title: "Is there a way to set up speed for mouse and touchpad individually?"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by mahy on 2007-03-17
Hi y'all,

i'd love to find a way how to configure my mouse and touchpad independently on each other. I know how to configure the touchpad in xorg.conf, but whenever i try to configure the mouse by means of 'xset m' (or any GUI frontend), it seems to affect the touchpad too. Please help. TIA.

---

### Post by jsully1 on 2007-08-17
Here are the relevant sections you need to edit in /etc/X11/xorg.conf to let you do this:
```

Section "InputDevice"
        Identifier  "Trackpoint"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"  
        Option      "Emulate3Buttons" "true"
        Option      "EmulateWheel" "true"
        Option      "EmulateWheelButton" "2" 
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MaxTapTime" "0"  #disables tap to click, I find it annoying
        Option          "MinSpeed" "0.05"
        Option          "MaxSpeed" "0.2"
        Option          "AccelFactor" "0.01"
EndSection

```

Your devices may have different identifiers, but the gist is the same - just add the bits about Min and Max speed and Accel to your touchpad section, and use the gnome configurator to set the trackpoint speed as you usually do.

Also, as an aside, the bits I have in the trackpoint section let you properly scroll with the middle button, and let it function as a middle click as well so you middle click on a tab to close it, or middle click a link to open it in a new tab.

---

### Post by buntubunny on 2007-12-22
The latest release version of gsynaptics (at the moment it is version 0.9.13) allows you to set the Acceleration, Min Speed and Max Speed graphically. It's available at:
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

However right now it is only available as source code. So after getting it you need to do the usual compilation from source. (i.e. ./configure, make, sudo make install, make clean)

(I did this on Ubuntu version 7.10 Gutsy Gibbon.)


Before using it, you need to set Option "SHMConfig" to "true" in /etc/X11/xorg.conf, under the "InputDevice" section where "Synaptics Touchpad" is identified.

Here's the relevant section of /etc/X11/xorg.conf:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"

        # This is for gsynaptics to control the touchpad
        Option          "SHMConfig"             "true"

EndSection

```

Hope this helps anyone else who needs this functionality.

---

