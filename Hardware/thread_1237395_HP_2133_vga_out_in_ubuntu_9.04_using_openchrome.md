---
title: "HP 2133 vga out in ubuntu 9.04 using openchrome"
date: 2009-08-11
forum: Hardware
---

### Post by artaman on 2009-08-11
Hi all,

This question has been asked many times (and got some answers/suggestions), still though by following them i haven't managed to make an external monitor work properly for me. Probably it's due to my lack of expertise in linux...

When connecting an external monitor on my HP 2133 (1280x768 native resolution) after a fresh install of ubuntu 9.04 I didn't get any output. That was expected due to the openchrome driver.

I then installed the latest svn version (773) of the openchrome driver (as suggested in some posts in the internet) hoping to get something different, still though no output (booting with the external monitor plugged in didn't make any difference). 

By adding the option "ActiveDevice" "LCD, CRT" in the Device section of xorg.conf i get a clone of the LCD on the external monitor, however xrandr doesn't work with openchrome and doesn't recognise the external monitor (just returns the lcd screen even when the external one is plugged in) so i cant fix the resolution on the external monitor to its nominal value (1280x1024).

By adding "Virtual 1280 1024" at the Display SubSection of xorg.conf i get the option to set the resolution to 1280x1024, but for some reason whereas it should -i would expect- match the external monitor perfecly, it still doesnt. The projected display is again stretched and exceeds the boundaries of the external monitor, the same way it exceeds the boundaries of the lcd...as if the external output tries to duplicate exactly what is visible on the lcd screen at all times.

Am i doing something fundamentally wrong here? If someone has indeed managed to have an external monitor operating properly at a resolution higher than what the internal lcd can support natively, could they drop a line here with their solution?

Many thanks for any answers

---

