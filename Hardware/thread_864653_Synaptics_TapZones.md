---
title: "Synaptics TapZones"
date: 2008-07-19
forum: Hardware
---

### Post by thegodfaza on 2008-07-19
My laptop uses a Synaptics Touchpad and when it used to run windows I could set up areas of the Touchpad to emulate buttons.(Mouse 4 & 5) Is it possible to also have tapzones in Linux?

---

### Post by A. J. Rimmer on 2008-07-20
I did quite a bit of tweaking on my touchpad settings quite a while back, but I think I have forgotten more than I ever knew about the subject!

But, in case you have not seen these, here are some links that might get you started in the right direction, at least to see if it is possible to do what you want:

[http://ubuntuforums.org/showthread.php?p=975421](http://ubuntuforums.org/showthread.php?p=975421)

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by dizee on 2008-07-20
it is possible to set up tapzones in linux. you need to edit your /etc/X11/xorg.conf file.
```
...
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
[I]        Option          "LeftEdge"      "1600"
        Option          "RightEdge"     "5400"
        Option          "TopEdge"       "1700"
        Option          "BottomEdge"    "4400"
[/I]      [B]  Option          "RTCornerButton" "0"
	Option          "RBCornerButton" "2"
	Option          "LTCornerButton" "0"
	Option          "LBCornerButton" "3"[/B]
        Option          "SHMConfig"     "on"
        Option          "Emulate3Buttons"       "on""
EndSection
...
```
*optional - define the size of the side boundaries*
**use corners for tapping - 0 = off 1 = left click 2 = middle click 3 = right click **

however even without setting up these tapzones, with the "Emulate3Buttons" "on" setting, you can usually get middle clicks by tapping two different points simultaneously and right clicks by tapping three points or once on the bottom right corner (this might be set up already, try it).

(i'm not sure if it can be set up for buttons 4 and 5 though.)

this thread is in the mac forum but it applies universally and has useful info: [http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

might be of use also: [http://ubuntuforums.org/showpost.php?p=5402634](http://ubuntuforums.org/showpost.php?p=5402634)

---

### Post by ugm6hr on 2008-07-20
This gives all the necessary controls:
```
man synaptics
```

---

