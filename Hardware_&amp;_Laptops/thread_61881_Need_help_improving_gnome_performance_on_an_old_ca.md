---
title: "Need help improving gnome performance on an old card"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by Roybotnik on 2005-09-02
Hi everyone,

I'm running 5.04 on a PC with the following specs:

800mhz Pentium III
512mb PC133 memory
8mb onboard Trident Cyberblade i1 video card

It seems as though when I do _anything_ in gnome, the CPU usage jumps up a lot.  I'm currently using the trident driver for xorg, and I've tried the VESA driver, both have the same results.  Even scrolling down through a window in firefox causes the CPU usage to spike to 100% and my display lags as if it's redrawing the entire image any time I make a change.  This happens any time I drag a window, minimize, maximize, etc.  I basically can't use my system because of it.  

Here are the entries being loaded under the Module section in xorg.conf:

bitmap
dbe
ddc
dri
extmod
freetype
glx
int10
record
type1
vbe

I don't have any special effects or anything enabled in gnome.  Any help would be greatly appreciated!

---

### Post by az on 2005-09-02
"Even scrolling down through a window in firefox causes the CPU usage to spike to 100% and my display lags as if it's redrawing the entire image any time I make a change. This happens any time I drag a window, minimize, maximize, etc. I basically can't use my system because of it. "

With your specs, you should have a zippy system.  You should not have any performance issues!   I do not think that the video card is the culprit.  The ubuntu desktop only uses 2d rendering, so an older card will only limit your maximum resolution and color depth.  But that should not have an impact on performance.

*Possibly* if you are using the framebuffer, it can sow down your system, but I do not think to the degree you describe.

If you run "top" in a terminal, and play around with your system, you can see what applications are hogging cpu power.  What app jumps to the top of the list when you scroll around in firefox?

From a terminal, run 

top

Another throught would be DMA, but you should not be using your harddrive to scroll around in firefox...

---

