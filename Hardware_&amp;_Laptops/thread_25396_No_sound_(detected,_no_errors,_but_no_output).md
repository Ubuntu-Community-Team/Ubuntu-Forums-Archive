---
title: "No sound (detected, no errors, but no output)"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by sreid on 2005-04-10
Mpg123 and totem run just like they're playing mp3/ogg/divx just fine, except I can't actually hear anything. SB Live (emu10k1 driver). 

Lots of possibly relevent command output is here (lsmod, amixer, etc.):
[http://www.sreid.org/soundproblem/](http://www.sreid.org/soundproblem/)

Everything is plugged in, and sound was working fine yesterday (Debian with 2.4 kernel, OSS). I installed Ubuntu 5.04 today and sound does not work. The first thing I noticed was that it detected my on-board sound first (ye olde Debian didn't detect it at all), so I disabled that (jumper on the motherboard) and now the SB Live is the first device, but still no sound. Could the on-board sound being present then removed have confused things?

The obvious thing would be a mixer setting at 0 volume or muted. I've looked at the mixer stuff (the gnome volume control, and alsamixer) and there is nothing obviously wrong, but there are dozens of controls that can be enabled in the gnome volume control and I can only identify a few of them. I don't want to simply crank all of the levels, as some items appear to be something other than volume-related (like "EMU10K1 PCM Send" and "EMU10K1 PCM Send Routing" - both have 32 controls, with 12 sliders per control).

Any suggestions?

---

### Post by Hinko on 2005-04-10
I still have problems with my sound blaster live. Though I managed to partially fix that (actually, for some reason Kaffeine works, though Knotify doesn't) . 

With XMMS you can choose the sound device as well as the drivers, fiddle around with that, see if there's any sound.

---

### Post by sreid on 2005-04-10
Oops! Looks like I was plugged in to the wrong jack.

I think the jack it outputs to has changed. Either that, or I had some other problem and tried another jack in my efforts to fix it but forgot to switch back, and since solved the original problem.  :|

---

