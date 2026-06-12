---
title: "Synaptics touchpad and 8.10"
date: 2009-01-10
forum: Hardware
---

### Post by Evil Overlord on 2009-01-10
Ubuntu 8.10
Gateway 7422GX with Synaptics touchpad

Problem: Touchpad is erratic and probably too sensitive.
Previous posts and pages suggest 
 a) install gsynaptics [done]
 b) don't mess with xorg.conf [since 8.04]

However, when I try to run gsynaptics, it tells me that I have to enable  in xorg.conf or XF86Config.

I tried adding "SHMConfig" "True" as recommended, just as a line by itself.  On restart, I had no GUI at all, and had to edit xorg.conf with vi.  I also tried adding [COLOR="RoyalBlue"]
[COLOR="RoyalBlue"]Section "Touchpad"
    "SHMConfig" "True"
EndSection[/COLOR][/COLOR]
which didn't work either.

I looked at 
[COLOR="DarkOrchid"]http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Configuration_via_xorg.conf_.28hotplugging_disabled.29
[/COLOR]
as one post recommended, but that seems a hell of a lot of work.  And in any case, I'm now leery of touching xorg.conf at all.

Advice?

My entire xorg.conf (minus comments):
ection "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

