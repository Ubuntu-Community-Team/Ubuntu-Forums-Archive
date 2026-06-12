---
title: "Where are my nvidia settings?"
date: 2016-08-07
forum: Hardware
---

### Post by Evil Wayz on 2016-08-07
I upgraded my kernel from 4.4 to 4.7 to fix some issues.  To do that I had to remove the nvidia module first.  When I added it back, I no longer get the splash screen, and these are all the settings I get when I open the nvidia settings program:

[IMG]http://i64.tinypic.com/15wgugp.jpg[/IMG]

Reverting back to 4.4 doesn't help.  I have basic resolution, and my panels are all gone.

---

### Post by Evil Wayz on 2016-08-09
New issue, I have two monitors hooked up to the card.  When I hook up hte monitor to the vga output it works, at a very low resolution, but when I plug in the hdmi, it turns off and refuses to be detected even by the "Displays" app.

---

### Post by mc4man on 2016-08-09
Probably because the nvidia modules didn't install. Try removing (purging) & then re-install from a terminal or synaptic & read thru the install console output to see what's happening

(- you could also ck. System Settings > Details to see what's being used for graphics

---

