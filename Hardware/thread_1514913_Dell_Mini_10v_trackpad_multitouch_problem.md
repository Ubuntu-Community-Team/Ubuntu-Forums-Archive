---
title: "Dell Mini 10v trackpad multitouch problem"
date: 2010-06-21
forum: Hardware
---

### Post by invisiblerhino on 2010-06-21
Hi guys,
I've been trying (and failing) to get multitouch working on my Dell Mini 10v. The closest I've got to it is with 
```

%> xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
%> xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
%> xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
%> xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

```
This doesn't, however get it to work, it just means I can sometimes get it to start edge scrolling, then convert that edge scroll into a two-finger scroll on the right-hand side of the trackpad.

Any ideas?

Ubuntu netbook remix, Lucid Lynx
I have gsynaptics if that might alter things.

Also noteworthy is that the option for two-finger scrolling is delayed in Preferences/Mouse/Touchpad.

Cheers

---

