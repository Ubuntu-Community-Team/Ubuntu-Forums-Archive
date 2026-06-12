---
title: "Problems with gartsize option and file r300_render.c"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by eheheh on 2008-01-17
I've an ATI graphics card and I use the open source drivers, the defaults in Gutsy Gibbon 7.10. With these drivers Compiz works (I can move the cube).
But while doing some 3D figures in Matlab I have these warnigs on the shell:

*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 470
Software fallback:ctx->Line.StippleFlag
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_mem.c function r300_mem_alloc line 225
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************

The result is that I can't save my figures in EPS format (I get black pictures) or my figures disappear while they still are in the window (before saving). Following the steps I found in a post of this forum, I added the gartsize option in my xorg.conf file: 


$ sudo nano /etc/X11/xorg.conf

Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "GARTSize" "64"
EndSection

I chose "64" instead of 128 (my real graphic card ram) because otherwise I coudn't have compiz working.
In this way I got only the first warning:

*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 470
Software fallback:ctx->Line.StippleFlag
***************************************************************************

Pictures don't disappear in the windows, but I still can't save them in EPS with compiz on. If compiz is off I can save them.
I suppose I've simply to add another option (but I'm a beginner, I'm having linux for only a month) like gartsize ring...
Sorry for my English, I'm Italian, but I hope someone will understand and help me.

---

