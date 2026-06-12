---
title: "Can't reduce screen resolution"
date: 2013-09-12
forum: Hardware
---

### Post by 6QXLBpz on 2013-09-12
I tend to give presentations in my laptop, which means reducing the resolution of my screen and then using twinview/cloning (kind-of an awful way to do this, I know, but there are reasons...)

It used to be easy to do reduce the resolution of my laptop screen; I would open nvidia-settings and change the resolution under X Server Display Configuration, but suddenly all resolutions except 1920x1200 have disappeared.  I tried the xrandr approach and got the following error:
```

$ xrandr --fb 1024x768
xrandr: specified screen 1024x768 not large enough for output LVDS-0 (1920x1200+0+0)
xrandr: Configure crtc 0 failed
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  21 (RRSetCrtcConfig)
  Value in failed request:  0x0
  Serial number of failed request:  37
  Current serial number in output stream:  37
```

Does this mean it's impossible to do this with the current version of the driver?  I'm using Ubuntu 12.04 on an NVidia 260m with driver version 304.88.

---

