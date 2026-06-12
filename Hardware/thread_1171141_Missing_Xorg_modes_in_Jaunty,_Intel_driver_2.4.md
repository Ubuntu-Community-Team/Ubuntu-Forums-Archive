---
title: "Missing Xorg modes in Jaunty, Intel driver 2.4"
date: 2009-05-27
forum: Hardware
---

### Post by gwiener on 2009-05-27
Hello everyone,
I have Jaunty running on a Dell laptop with an Intel graphics card. Due to some performance problems, I've already reverted the driver to version 2.4 using [these instructions]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4"). I have a standard xorg.conf file, listed below.

The problem: The laptop screen has only one mode, both in xrandr and when using the display configuration tool. "xrandr -q" outputs only:
```
LVDS connected (normal left inverted right x axis y axis)
   1440x900       60.0 +

```

This problem does not effect external screens, only the LVDS screen. However, I need more display modes in order to use "mirror screens" with an external projector.

How can I get the missing display modes? Preferably without modifying xorg.conf too much, but I can do that if necessary.

Thanks,
  Guy.

Here's my xorg.conf:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver "intel"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
EndSection

```

---

### Post by downwa on 2009-07-06
I'm having the same problem (missing modes in Jaunty, Intel driver 2.4) and was wondering if you or anyone else has resolved this issue.

In my case, the use of the 2.4 driver is not just a performance issue, but due to random freezes (others have experienced this too and recommended using the older driver until it's resolved).

In any case, I'd like to be able to change to lower resolutions than the laptop's maximum resolution, e.g. for games which run better at lower resolutions.

---

