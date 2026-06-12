---
title: "Since upgrading to koala my touchpad is unhappy"
date: 2009-10-16
forum: Hardware
---

### Post by phorgan1 on 2009-10-16
I'm having problems since upgrading to koala.  I'm not having the problem that many report about not being able to click on the pad.  That works fine.  It's that the edge scrolling doesn't work unless I turn it on manually via synclient. 

In my /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi I have the following uncommented.
```

        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">true</merge
```

Yet when using synclient -l I'm told that for instance:

```

VertEdgeScroll          = 0
VertTwoFingerScroll     = 0

```
After using synclient to turn them on, vertical edge scrolling works, but not the two finger scrolling. But of course that's only temporary and they are off next time I boot.  Sytem/Preferences/Mouse/Touchpad/EnableVerticalScrolling is selected.

Help!

---

### Post by Brandel Valico on 2009-10-16
Had the same problem, fixed it by going to system,Prefrences,startup applications and creating a new startup command. Labeled Touchpad fix. In the command line I have this "synclient RightEdge=5932" You may need to play around with the 5932 number to set it to you own prefrence. But it does work. 

Note: I still on occasion have to goto the scroll bar on boot up in say firefox and use the touchpad to move the screen once. But when done scrolling kicks back in for the entire session. Not a complete solution but a decent workaround for now.

---

