---
title: "persistent tapping"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by eastern_strider on 2006-11-09
I've been trying to disable the tapping behavior of my trackpad for some time now. I've tried to edit my xorg.conf file in the following ways:

```

  Option    "MaxTapTime" "0"

```

```

Option    "tapbutton1" "0"

```

The rest of my xorg.conf file is as follows:

```

 Identifier  "Synaptics Touchpad"
  Driver    "synaptics"
  Option    "SendCoreEvents"  "true"
  Option    "Device"    "/dev/psaux"
  Option    "Protocol"    "auto-dev"
  Option    "HorizScrollDelta"  "0"
  Option    "SHMConfig"   "on"

```

However, with either approach the tapping seems to be disabled temporarily but it just then gets activated by itself. I'm not sure if an application is causing this.

Any suggetions?
Thanks

---

### Post by A. J. Rimmer on 2006-11-09
Drives ya crazy, right?

I tried setting SHMConfig on so that I could use Qsynaptic, but I couldn't make the Qsynaptic settings stick, so I removed that line and tried setting MaxTapTime to 50.  If I'm very careful and make a very deliberate, soft touch, I get the "tap to click" function, otherwise the tap is ignored.  Don't know if that would help in your situation or not, but you might try it.

I'm using an HP dv5000-series laptop.

---

### Post by eastern_strider on 2006-11-10
I've tried your suggestions and it seems to work pretty good. Since doing that I haven't accidentally tapped on the trackpad :)

Thanks for this practical solution. By the way I'm using a Toshiba laptop.

---

### Post by eastern_strider on 2006-11-11
An interesting observation. When I restart my xserver using **ctrl + alt + backspace** trackpad tapping gets disabled if I have one of the following commands in xorg.conf:

```
Option    "MaxTapTime" "0"
Option    "tapbutton1" "0"
```

However, when I make a fresh restart mouse tapping gets enabled again. In both situations xorg.conf is read in the same way (I guess). There must be something that happens after xorg.conf is read that enables mouse tapping again. I think something is overriding these commands in xorg.conf.

Any ideas?
eastern_strider

---

