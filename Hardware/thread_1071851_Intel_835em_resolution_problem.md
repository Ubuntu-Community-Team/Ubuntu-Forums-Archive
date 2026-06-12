---
title: "Intel 835em resolution problem"
date: 2009-02-16
forum: Hardware
---

### Post by Redeyes_Gambit on 2009-02-16
I have an old Sony Vaio sub-notebook with an Intel 815em video chip I am trying to resurrect, and so far things have gone reasonably smooth. One persistent niggle remains in the form of being stuck at 800x600. I tried some of the fixes but I fear the problem may be deeper than a change to xorg on this one.

I edited my xorg to add the 1024x768 resolution, but whenever I set it to 1024x768 I have no video (black screen of doom). A reboot to revovery-ville and a repair of xorg later and I have picture again but only at 800x600.

I know the chip supports up to 1024x768 because when XP was on the machine I had that res. Also, the picture doesn't scale up at lower resolutions, it just uses a smaller portion of the screen. Lol, a 10" sub-notebook using only a portion of it's miniature screen is somewhat less than pleasant to use.

I was wondering if the driver perhaps does not support the res, and if there is anything I can do about it?

*EDIT*

OOPS, I see this has already been thouroughly discussed at [http://ubuntuforums.org/showthread.php?t=891327&highlight=815](http://ubuntuforums.org/showthread.php?t=891327&highlight=815) . Don't Know how I missed this one on previous searches. Too bad it looks like it is still unresolved.

*EDIT 2*

Lol, never fails, you post a question just before discovering the answer. Check out [http://ubuntuforums.org/showthread.php?t=998642&highlight=815](http://ubuntuforums.org/showthread.php?t=998642&highlight=815) if you are having this problem. I copy-pasted the xorg (preserved below for posterity) and VIOLA! 1024 resolution is mine!

> Section "Device"
Identifier "Configured Video Device"
Option "RenderAccel" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 31.5 - 50.0
VertRefresh 40-90
Option "UseEdidFreqs" "1"
Option "ReducedBlanking"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection

EndSection

---

