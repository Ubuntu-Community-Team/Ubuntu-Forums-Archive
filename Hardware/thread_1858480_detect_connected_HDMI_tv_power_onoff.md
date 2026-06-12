---
title: "detect connected HDMI tv power on/off"
date: 2011-10-12
forum: Hardware
---

### Post by mr-zap on 2011-10-12
Hi,

I'm looking for a way to find out in a script whether a TV attached over HDMI is powered on or off. This is for a HTPC arrangement - the plan is to turn the computer into a headless internet radio when the TV is powered off. I'm not interested in setting up a shortcut key.

The missing link so far is detecting when the connected TV is powered on or off (by off I mean in standby). So far I've tried:

- xrandr
- get-edid / parse-edid
- ddcprobe
- aplay -l
- some digging in /proc/asound/Intel

none of which seem to give different output when the TV is on or off.

There's a utility called disper which sounds like just what I need, but my intel GMA graphics aren't supported ("No suitable backend found").

would be really grateful for any suggestions.
thanks a lot!

---

