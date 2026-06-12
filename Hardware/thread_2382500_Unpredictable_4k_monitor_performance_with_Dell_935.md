---
title: "Unpredictable 4k monitor performance with Dell 9350"
date: 2018-01-14
forum: Hardware
---

### Post by kfholbrook on 2018-01-14
I have a Dell XPS 9350 with integrated Intel Sky Lake graphics. When I plug my external Samsung 4k D590 into the laptop via USB-C to HDMI and close the laptop the monitor works at 4k (3840x2160). After a few minutes the monitor will flicker and revert to 1920x1080 and the 4k resolution is no longer available in xrandr. When I attempt to add it back with xrandr the monitor goes to unreasonably low unusable resolution. If I restart the laptop the 4k resolution works again.

I've tried various googled solutions for similar problems over the last two days instead of working. I would appreciate any help.

---

### Post by DuckHook on 2018-01-14
Welcome to the forums, kfholbrook.

What version and flavour are you using?

Please post results of:```
xrandr
```Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Please post one result with laptop closed (no problem), and another with lid open (when problem is present).

USB-C to HDMI is known to cause problems. The problem could be HW-related: possibly a poor wire or the USB port. However, your problem seems more complex as it doesn't manifest with lid closed, but only when lid open. Therefore, also post results of:```
lsusb
```

Note that I'm of limited help. I don't run USB-C to HDMI. Hope that a video guru dives in here. I will say that you've chosen a particularly ornery combo. USB-C video is finicky and HDMI has all sorts of DRM junk that monkeys with signals. Is it possible to connect without all of that conversion? The best would be DP to DP or, if you must use HDMI, then HDMI to HDMI.

---

