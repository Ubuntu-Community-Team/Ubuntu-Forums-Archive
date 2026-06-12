---
title: "Cannot change touchpad preferences or load synaptic"
date: 2011-05-10
forum: Hardware
---

### Post by CronoDekar on 2011-05-10
This is for Lucid Lynx, using a new HP Pavilion g6 laptop:

My touchpad is working just fine -- including touchpad features, but I haven't been able to update any touchpad settings.  "Mouse Preferences" doesn't show a "Touchpad" tab, and gsynaptics says I need to set SHMConfig to true in xorg.

From synclient -l I get: "Couldn't find synaptics properties. No synaptics driver loaded?"

From syndaemon I get: "Unable to find a synaptics device."

Here is the relevant section of my /usr/lib/X11/xorg.conf.d/10-synaptics.conf:


```
Section "InputClass"
	Identifier "touchpad catchall"
	Driver "synaptics"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Option "SMHConfig" "true"
EndSection
```

I've tried a variety of solutions I've found through many Google search, but I have not been able to get anything to work.  If anyone here could help, they'd be a godsend!  I'm so tired of the touchpad being so sensitive that it keeps moving my pointer position when I type.

---

### Post by CronoDekar on 2011-05-11
Oh, one thing I almost forgot -- here's the result of my xinput -list:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam-101                           	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

Which shows that my touchpad has been identified (most of the stuff I've found online doesn't identify the touchpad -- those solutions haven't been of any help to me)

---

### Post by Sam Lars on 2011-05-24
Maybe you already found this, but it has some good info:
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)
Also, of course, you could try Natty, the latest Ubuntu version, to see if it works any differently.
I'm having the same thing on a different laptop... from the above guide, it is evidently a problem with HAL.

---

