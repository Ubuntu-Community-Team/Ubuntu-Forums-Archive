---
title: "HOWTO: Disable the touchpad lag"
date: 2010-01-05
forum: Hardware
---

### Post by SKLP on 2010-01-05
Background info:

When X has Emulate3Buttons enabled for an input device, it will wait a while before allowing a normal click (to check if it is a left+right click which then is interpreted as a middle click). This lag can be very irritating in normal computer usage (at least it is for me, and also for some people I know).
Fortunately, X disables the emulation automatically (for a specific input device) as soon as it detects a real (non-emulated) middle-click. (Really, it should be done as soon as the mouse is plugged in, if it detects the correct number of buttons. It's sort of a bug i guess.)

But some users (like me) might like to disable it even for devices which do not have a middle-button (most touchpads for instance).
Previously it could be disabled using xorg.conf, but with the newer X input stuff it has to be disabled either using (afaik) hal or for the session using "xinput". But hal is being deprecated.
So I want to show how it can be done using xinput.

Howto:

We can use xinput to set the timeout that's used for middle-button emulation to 0, effectively disabling the emulation altogether.

We can get the current value of the property like this:
```
$ xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Middle Button Timeout"
	Synaptics Middle Button Timeout (242):	75
```
As you can see, the default value is 75. 

We are going to set it to 0, we can do as follows:
```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Middle Button Timeout" 32 0
```

But it will only be gone for the current session, so you can add it to start on login if you wish (in Preferences -> Startup Applications).

We are done ;)

As a side note, it can be fun to temporarily set the latency property to some high value (e.g. 1000) to experience some real click-lag! 
It can be done in the same way except change the 0 at the end to 1000 ( or whatever) .

---

