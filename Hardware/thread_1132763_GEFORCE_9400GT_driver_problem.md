---
title: "GEFORCE 9400GT driver problem"
date: 2009-04-22
forum: Hardware
---

### Post by gewitty on 2009-04-22
I just installed 8.10 on a new machine, which has a Geforce 9400GTgraphics board.

The default Ubuntu driver (Open GL?) works fine and correctly sets my screen resolution to 1440x900 16:10. However, when I install the recommended Nvidia driver (177), I am unable to select a screen resolution above 640x480 4:3.

The driver seems to be OK in all other respects, because Compiz effects work.

Am I missing some setting somewhere, or is there a problem with this driver?

---

### Post by gewitty on 2009-04-24
I've got a bit further in diagnosing the problem, which appears to be connected with the DDI information supplied by the monitor. For some reason this is not being read by my system.

As an experiment, I disconnected the edge10 monitor and replaced it with my original Philips 170B4. The same problem was exhibited: When I open up the screen resolution utility, it does not recognised the make or model of the monitor. For some reason, it does get the resolution and format (4x3 or 16x9) for both screens. Pressing the 'Detect Displays' button has no effect either.

As a final test, I hooked the edge10 screen up to a completely different PC. This one has 8.10 installed, but uses an ATI RagePro 9800 graphics board. Exactly the same situation was reproduced, which leads me to conclude that the fault is with the OS, not the monitor(s).

I did also check the xorg.conf file, to ensure that DDI was not disabled.

So that's as far as I've got. Does anyone have any thoughts on how I can rectify this, because until I do, I've got a fairly expensive graphics card sitting around doing nothing much at all.

---

### Post by gewitty on 2009-06-09
The problem was that the Nvidia driver was not reading the EDID information being sent by the monitor. This caused it to revert to a basic VESA setup.

The solution was to get a copy of the raw binary EDID file from the manufacturer (Edge10) and force the Nvidia driver to use this by modifying the Xorg.conf file, as per the Nvidia ReadMe (Appendix B) instructions.

This involves adding the following line to the Device section of the Xorg.conf file:

Option "CustomEDID" "DFP:/tmp/edid.bin"  (or whatever your filename and path actually are).

This obviously works for pretty much any Nvidia card and any monitor where the EDID information is not being read correctly.

Hope that helps anyone else who's been tearing their hair out with the same problem.

---

