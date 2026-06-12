---
title: "How to fix accidental click-drags with Logitech T650 touchpad?"
date: 2016-03-13
forum: Hardware
---

### Post by jjramsey on 2016-03-13
Under Ubuntu GNOME 14.04.3 LTS, the touchpad sometimes treats what's supposed to be cursor movement as a cursor *drag*, so that I end up accidentally highlighting text, dragging icons that I didn't want to drag, and so on.

So far, I have not seen this misbehavior in live sessions of CentOS 7 and Fedora 23, which also don't enable some of the "nice" behavior that Ubuntu does, such as two-finger scroll. I've noticed that neither of those Linux distros use the synaptics driver with this touchpad either (so running "synclient -l" yields nothing in those distros, whereas it does show a list of option settings under Ubuntu). I suspect that the "help" I'm getting from synaptics may be causing trouble, but I'm not sure.

Is there a way I can get this touchpad to work properly?

[ETA: Finally got the firmware for this trackpad updated. The touchpad still seems to have the problems that I had mentioned before.]

ETA:

I think I've found a solution.

First off, an attempted solution that didn't quite work, namely setting TapAndDragGesture to 0 with synclient. This seems to have gotten rid of the most egregious behavior, but there still seemed to be instances where I still got unwanted drags.

However, simply disabling tap-to-click seems to work. The catch seems to be that a physical click does seem to take a bit of force, and that does seem to wear out my wrists more easily, but your mileage may vary on that (given that I do have some RSI.)

---

