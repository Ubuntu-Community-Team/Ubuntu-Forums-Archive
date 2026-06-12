---
title: "DPMS not working on Libretto (Possible NeoMagic driver bug?)"
date: 2008-06-26
forum: Hardware
---

### Post by Doc5 on 2008-06-26
I've an ancient Libretto 110ct with Ubuntu 8.04 installed.  Everything works pretty well, but I have not ever been able to disable the backlight using Xorg or virtual terminal DPMS support.

I've tried changing settings while in a virtual terminal using setterm, and the screen will blank, but it will not turn off the backlight.  A similar situation happens in Xorg.  I've tried using xset to set a timeout for a DPMS powerdown, and the screen just blanks.  The same thing happens if I perform a "xset dpms force off". 

"vbetool dpms off" does successfully disable the backlight, so I'm reasonably certain it's not a hardware issue, but I don't particularly like the thought of having to issue commands to enable/disable the screen all the time.

I'm mostly concerned about the screen refusing to sleep in Xorg, since that's probably where I'll be most of the time.  DPMS is, according to the man page, enabled by default in Xorg, but I've manually added

Option "DPMS" "On"

and nothing changed.  What else can I try?

---

