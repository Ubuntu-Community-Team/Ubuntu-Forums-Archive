---
title: "Screen doesn't get locked every time I close the laptop lid"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by J.Vega on 2007-01-28
Hi,

I have a laptop with Ubuntu edgy set up. Using the gnome-power-manager, I configured Gnome to "blank" the screen when I close the laptop lid. The first time I do so, it locks the screen and when I open the lid again, it prompts me for a password. That's exactly the way I want it to be. The problem is, that it seems to remember this and doesn't ask me for a password if I close the lid again. I don't want the laptop to go in standby or hibernate mode when I close the lid, but except those two and the "blank screen", there's no option to select in the gnome-power-manager configuration window.
I already tried to hack the settings with gconf-editor, but I didn't find an option which would change this behaviour. I tried activating lock_use_screensaver_settings but I as far as I can judge this, the screensaver needs at least 1 minute to lock the screen.
lock_on_blank_screen is activated (and lock_use_screensaver_settings deactivated), but it doesn't really seem to lock my screen every time. When I open the lid after closing it the second time, the screen isn't really black, it's just very dark (i guess the light behind the lcd panel is just turned off).
Is there any "timeout" which prevents gnome from locking the screen after I unlocked it? And if yes, how do I deactivate it?

---

