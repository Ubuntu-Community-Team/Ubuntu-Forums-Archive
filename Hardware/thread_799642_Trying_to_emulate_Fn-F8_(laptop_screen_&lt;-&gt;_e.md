---
title: "Trying to emulate Fn-F8 (laptop screen &lt;-&gt; external display) with Linux/NVidia"
date: 2008-05-19
forum: Hardware
---

### Post by enbuyukfener on 2008-05-19
Using a mostly stock Ubuntu install with 169.12 NVidia drivers installed, Fn-F8 is not working (this hot-key is commonly found on laptops to switch between the laptop screen and the external display and maybe a dual view mode, e.g. TwinView or clone/mirror)

On Windows and before X starts, the hot-key works, and other Fn combinations such as Fn-F1 for sleep and Fn-F3 for battery/power status work in Ubuntu.

I wouldn't mind experimenting with metamodes and bash scripts even if it means I have to use a different hot-key.

Considerations:
- the laptop runs at 1280x800, the external monitor runs at 1440x900 or 1680x1050
- the laptop screen seems to only work with some configurations, sometimes requiring a custom EDID, otherwise it turns into a white screen with a black vertical bar about 2/3 across about 1/6 of the screen wide. I've never been able to isolate this problem and it has been a problem with the Ubuntu gutsy installer GUI (hardy was fine) and a GPartEd live CD where I needed to force usage of the "vesa" driver

I am about to use this as a starting point:
[http://ubuntuforums.org/showthread.php?t=634675](http://ubuntuforums.org/showthread.php?t=634675)
However it was problematic for this guy so it'd probably be just as bad (if not worse!) for me.

Thanks in advance for any help.

---

