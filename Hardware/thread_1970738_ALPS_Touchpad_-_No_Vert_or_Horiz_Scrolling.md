---
title: "ALPS Touchpad - No Vert or Horiz Scrolling"
date: 2012-05-01
forum: Hardware
---

### Post by dodle on 2012-05-01
I've got an HP dv4-1281us with an ALPS touchpad #-o. I've installed the [psmouse-alps package](http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb) and it is working well except that there is no scrolling. These are the steps that I took to install the driver: [http://okle100.blogspot.com/2012/02/configure-touchpad-disable-button-on.html](http://okle100.blogspot.com/2012/02/configure-touchpad-disable-button-on.html). I am running Debian 6.0.4 Squeeze.

```
:~$ uname -r
2.6.32-5-amd64
```

Any ideas on how I can get the scrolling to work? I've tried a few different things including installing a patched psmouse.ko. I've tried adding the synaptics driver options to my xorg.conf but it does not help:

```
Section "InputClass"
        Identifier       "enable synaptics SHMConfig"
        MatchIsTouchpad  "on"
        MatchDevicePath  "/dev/input/event*"
        Option           "SHMConfig" "on"
# Device option should not be required
#       Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
	Option      "SendCoreEvents"
        Option      "SHMConfig" "on"
	Option      "TapButton1" "1"
	Option      "TapButton2" "2"
        Option      "Emulate3Buttons" "yes"
        Option      "LeftEdge" "120"
        Option      "RightEdge" "830"
        Option      "TopEdge" "120"
        Option      "BottomEdge" "600"
        Option      "FingerLow" "14"
        Option      "FingerHigh" "15"
# Set MaxTapTime to 0 to disable tapping
#       Option      "MaxTapTime" "0"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "110"
        Option      "VertScrollDelta" "20"
        Option      "HorizScrollDelta" "20"
        Option      "AccelFactor" "0.030"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "1.0"
EndSection
```

Are there some options that I can add to the /etc/modprobe.d/psmouse.conf file?


**----- SOLVED -----**

Here is what I did to get it to work:

First of all, here is part of my current xorg.conf (not exactly sure what all is important here):
```
...
Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputClass"
        Identifier       "enable synaptics SHMConfig"
        MatchIsTouchpad  "on"
        MatchDevicePath  "/dev/input/event*"
        Option           "SHMConfig" "on"
EndSection

Section "InputDevice"
        Identifier  "Touchpad"
        Driver      "psmouse-alps"
        Option      "SHMConfig" "on"
# Device option should not be required
#       Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
	Option      "SendCoreEvents"
	Option      "TapButton1" "1"
	Option      "TapButton2" "2"
        Option      "Emulate3Buttons" "yes"
        Option      "LeftEdge" "120"
        Option      "RightEdge" "830"
        Option      "TopEdge" "120"
        Option      "BottomEdge" "600"
        Option      "FingerLow" "14"
        Option      "FingerHigh" "15"
# Set MaxTapTime to 0 to disable tapping
#       Option      "MaxTapTime" "0"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "110"
        Option      "VertScrollDelta" "20"
        Option      "HorizScrollDelta" "20"
        Option      "AccelFactor" "0.030"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "1.0"
EndSection
...
```

After installing the psmouse-alps driver, I opened /etc/modprobe.d/psmouse.conf and changed:
```
options psmouse proto=imps
```

to
```
options psmouse proto=any
```
Then I ran:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

Now the touchpad is working great along with edge scrolling.

Another note: To enable circular scrolling I did:
```
synclient CircularScrolling=1
```

Credit goes to [this thread](http://www.linuxquestions.org/questions/slackware-14/slackware-current-synaptics-touchpad-problem-732856/) for helping me find a solution.

---

