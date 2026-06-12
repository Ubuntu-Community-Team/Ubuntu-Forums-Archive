---
title: "[SOLVED] Samsung Syncmaster 204b flickers in Intrepid"
date: 2008-11-08
forum: Hardware
---

### Post by dummzeuch on 2008-11-08
Hi,

I just upgraded from Hardy to Intrepid and an already solved problem came back: My Samsung Syncmaster 204b (attached to DVI) has started to flicker again, when I run it at resolutions above 1280x1024.

I had solved that problem in Hardy by adding a custom modeline for the monitor, that reduced the refresh rate to less than 60 Hz using the proprietary ATI graphics driver version 8.10 (unfortunately I do not have a copy of that xorg.conf file any more, it got lost while I was trying different settings, I should have been more carefull :-( ).

That ATI driver no longer works with Intrepid, but that would be fine, because Intrepid brings its own, newer version of the driver, but it does not work. I tried several of the modelines suggested on the net (one of which must have been the one that worked with Hardy), but to no avail.

The graphics card is an "ASUS AH3650 silent" which has got an ATI chipset. (Of course it works under Windows, just as well as it did with Hardy).

"cvt 1600 1200 60 -r" outputs this:

# 1600x1200 59.92 Hz (CVT 1.92M3-R) hsync: 74.01 kHz; pclk: 130.25 MHz
Modeline "1600x1200R"  130.25  1600 1648 1680 1760  1200 1203 1207 1235 +hsync -vsync

But it does not work.

I have attached my current xorg.conf file. Please note that I have commented out the 1600x1200 resolution in the screen section, because otherwise I wouldn't be able to post this.

Does anybody maybe have a tested solution?

twm

---

### Post by dummzeuch on 2008-11-15
> **dummzeuch said:**
> 
I had solved that problem in Hardy by adding a custom modeline for the monitor, that reduced the refresh rate to less than 60 Hz using the proprietary ATI graphics driver version 8.10 (unfortunately I do not have a copy of that xorg.conf file any more, it got lost while I was trying different settings, I should have been more carefull :-( ).

That ATI driver no longer works with Intrepid, but that would be fine, because Intrepid brings its own, newer version of the driver, but it does not work. I tried several of the modelines suggested on the net (one of which must have been the one that worked with Hardy), but to no avail.

The graphics card is an "ASUS AH3650 silent" which has got an ATI chipset. (Of course it works under Windows, just as well as it did with Hardy).


ATI has released version 8.11 of their proprietary driver. I installed it and can now again use 1600x1200.

What did the trick was this modeline:

Modeline "1600x1200twm"	150   1600 1664 1856 2160   1200 1201 1204 1250  +hsync +vsync

(Note: I tried the same modeline with the driver that came with intrepid and it did not work.)

I have attached my xorg.conf just in case anybody else has the same problem.

---

