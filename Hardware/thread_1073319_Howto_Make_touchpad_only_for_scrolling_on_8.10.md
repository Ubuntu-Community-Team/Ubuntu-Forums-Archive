---
title: "Howto: Make touchpad only for scrolling on 8.10"
date: 2009-02-18
forum: Hardware
---

### Post by littlelion58 on 2009-02-18
I've been looking around to find a way to make the touchpad on a thinkpad laptop/other laptop with a nipple and touchpad only used for scrolling, after some searching i stumbled accross the answer myself, it's kind of a round about method, it's my first post, and i'm a noob really so don't shoot me down and sorry if this has already been posted.

Overview:

Enable SHMConfig

Install "Touchpad" from the repository

Set All values in "Accelleration" tab to 0

Other cool stuff :)

**Enabling SHMConfig**

open a terminal and type

```
 sudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

```

Find the line "<merge key="input.x11_driver" type="string">synaptics</merge>" and just after it add the line:

"<merge key="input.x11_options.SHMConfig" type="string">On</merge>"

save and restart, then go to add/remove and install the "Touchpad" App

run the application from System > Preferences > Touchpad, click on the accelleration tab and set all three bars as far left as they can go.

this should effectively dissable the use of a touchpad as a mouse without removing the scrolling functionality.

**Other stuff**

Two finger scrolling

Something i quite like is 2 finger scrolling and it can be enabled, along with other synaptic options inside the synaptics.fdi file, the blue text explains how to do this, but as an example, to enable 2 finger scrolling add the line "<merge key="input.x11_options.VertTwoFingerScroll" type="string">On</merge>" after the SHMConfig enable line.

if you then want to dissable the edge scrolling (leaving only 2 finger enabled), then go into System > preferences > Mouse and in touchpad uncheck the vertical scrolling box.

I hope this helps someone, and i'm sorry if this has already been posted.

Many thanks

Peter

---

