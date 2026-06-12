---
title: "TV not recognized"
date: 2009-07-24
forum: Hardware
---

### Post by daveldhu on 2009-07-24
Hi everyone,

This is a continuation of a post made in install/upgrades, but kind of progressed into more of a hardware issue so I'll post it here.

My issues is with my TV not being recognized by ubuntu through a DVI-HDMI connection. I can run a monitor ok and everything so there's no problem with drivers or video card or anything. 

When I connect the TV and boot up, all I get is a black screen, not even the BIOS screen shows up. When I hook up a VGA monitor at the same time and do dual display, everything works fine on the VGA monitor, but still nothing on the TV.

When I go into the display settings, the TV shows up in there as detected, but shows up as "LG 23" LCD" or something like that, when it's a Toshiba TV...

When I run 'xrand -q' it shows a monitor connected to the DVI-0 port.

Is there any specific options I need to include in my xorg.conf file? I've tried "ForceTVOut" and setting the mode to ntsc.

Any help at all would be greatly appreciated!

Thanks!

PS. Video card is an ATI X800

---

### Post by philcamlin on 2009-07-24
this may be stupid but is the connectors plugged into the tv correctlyand are you on video 1 etc...

just to rule out the stupid things :popcorn:

---

### Post by daveldhu on 2009-07-24
I certianly hope so :P

Lol yes they are, tried it with an XP computer and it worked like a charm, as well as with a different cable.

Thanks for the quick reply by the way!

PS. And when I say 'with a different cable' I mean it didn't work on ubuntu with a different cable, thus it's not the cable lol.

---

### Post by dlmarti on 2009-07-24
I saw this on my dad's setup, the video card doesn't start outputing on the HDMI cable until the screen resolution is compatible.

Your mileage may vary, but try a few different resolutions.

---

### Post by daveldhu on 2009-07-24
Thanks for the reply!

I figured this might be the problem, however it only gives me a few options for resolution (600X800 up to 1280X1024) And none of these work... Any idea what his xorg.conf file looks like? It doesn't seem to use the resolutions I enter into the mode, I think because it doesn't properly recognize the tv. Anyone know of a way I can force a resolution that doesn't show up in the display settings?

Thanks again!

---

