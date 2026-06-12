---
title: "laptop LCD (not external) won't enable in xorg with intel/i810 drivers"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by evultrole on 2007-12-24
So I have sort of an odd problem, and sadly it isn't the first time. It's actually exactly the reverse of what you'd expect.


**Here's my problem:**

i845g chipped laptop, works on external monitor but not internal lcd

internal lcd works fine in console mode and xorg with VESA drivers, simply does not work with newest i810/intel drivers.

xorg ignores my xorg.conf file, selecting a resolution unsupported by either monitor (onboard LCD and the monitor I'm using both max at 1024x768. It goes to 1280x1024 on the monitor, even though conf file specifies **only** 1024x768

xrandr -q lists me as only having VGA connection (no LFP/LVDS)

i810switch always shows lcd as off by default

[B]Using: Ubunto 7.10, default install (plus mesa-dri which was left out for some reason?)

I've tried:
[/B]
Setting my bios settings to BOTH displays instead of AUTO (doesn't have an LCD only option >.<) - doesn't change anything aside from cloning the console

i810switch - works if I turn the LCD off and on again, but still in 1280x1024 mode, so bottom and right side of screen are cut off and inaccessible. Restarting X or the computer puts the LCD back into "off" mode. not an acceptable solution.

Various combinations of the Option "Monitor-LVDS" switch, which changes nothing in any way.

Manually setting my LCD refresh rates and display sizes. Accomplished only losing 15 minutes of my life.

xrandr --display LVDS --on (or whatever the applicable command it, I'm not at the computer right now to look up syntax). Gave an error (makes sense since xrandr thinks I have no LCD).
[B]
Background info:[/B]

This retarded desktop chip in a laptop thing worked fine with Slackware and Gentoo up to roughly 13 months ago. 13 months ago I replaced gentoo with Ubuntu and gave the laptop to my Grandfather. Worked fine at the time. (I had been using it for 2 years prior, never had a problem with the display or acceleration). I assume it was in Vesa mode at the time, I didn't think to check.

I just upgraded the system to 7.10 (to add support for a network card he purchased). Booted the system, found it to be in Vesa mode (he asked about a flight simulator game so I bothered to check).

Switched to intel driver (first i810, then intel) to find neither works.

The screen craps itself when the i810 or intel drivers are in use, I guess forcing itself to think it's a desktop without a built in LCD. Acceleration works, which is a plus, it's just not really usable as a laptop  this way.

To rule out the upgrade as the culprit (not because I think it was, but that way nobody will suggest it) I went ahead and did a fresh format and install of 7.10. Still have the problem.


[I]Anyone else run into this or something similar and have any suggestions on something I can try (other than filing a bug report)?

And thanks for making it this far down, I tend to ramble: Sorry.[/I]

**edit:**

Just to clarify, the problem is that the internal LCD will not work in Xorg with the intel drivers, not that it doesn't work correctly. Vesa mode and console both work fine.

---

### Post by daengbo on 2007-12-24
Can you post the results of lspci?

---

### Post by evultrole on 2007-12-24
Nevermind on all of this. I downloaded the i810 driver from debian (the xorg 7.1 version, 1.7.2 vs 1.7.4 or some such) and all is happy again... though I still had to do the DisplaySize 286 215 thing and disable DisplayInfo to get it to work.

Dunno why the new driver does this, maybe it will get fixed by the time xorg 7.4 is released. At least I know it's a driver issue between i810 1.7.2 and 1.7.4 now, so... that's positive? .... unless my computer is just screwing with me and refusing the use the new drivers because acer is a crap company who never releases video bios updates.

Though now I have that stupid "You're software is outdated! Click to update!" thing pop up everytime the computer turns on.

C'est la vie

Thanks for the reply though!

---

