---
title: "Dual Display (thinkpad x61s, Intel Mobile 965 chipset)"
date: 2009-10-28
forum: Hardware
---

### Post by martinmaurer on 2009-10-28
hi all,

I am using 9.10 rc (32-bit) with an external monitor in extended desktop mode, working so far. but the primary desktop is my laptop display (the small one) and I want to change this to the 19 inch monitor (make the big one to the default, showing the gnome panels, etc.).

This can be done on windows with the intel graphic drivers. Also it can be done on my second thinkpad with the non-free nvidia tool without problems (here I have a nvidia graphic card).

How can I configure this with the intel card? the default display tool does not show this option.

thanks for any hint,

br, martin

---

### Post by uoirej on 2009-11-11
Instructions found [*here*]("http://gaarai.com/2009/11/03/move-gnome-panels-to-a-different-monitor-in-ubuntu/"):

 1. Right-click the panel you wish to move and select “Properties”.
 2. Uncheck the “Expand” option under the “General” tab.
 3. Grab one of the edges of the panel by clicking on the left or right end (top or bottom end for vertical panels).
 4. Drag the bar to the desired screen and position.
 5. Check the “Expand” option in the “Panel Properties” window and click “Close”.

After moving the panel with window list I had to resize the window list applet (is this really an applet? not sure) manually since it somehow shrinked to zero.

Hope this helps.

BTW, I don't think moving the panels has anything to do with video drivers. What else do you mean by "setting the default monitor"?

PS After playing a bit with panel positions, moved them back to the (smaller) laptop display. Why would I waste any pixel of the (bigger external) primary working display for not-always-needed info?

---

### Post by AndreasAichholzer on 2009-11-19
> **uoirej said:**
> Instructions found [*here*]("http://gaarai.com/2009/11/03/move-gnome-panels-to-a-different-monitor-in-ubuntu/"):

 1. Right-click the panel you wish to move and select “Properties”.
 2. Uncheck the “Expand” option under the “General” tab.
 3. Grab one of the edges of the panel by clicking on the left or right end (top or bottom end for vertical panels).
 4. Drag the bar to the desired screen and position.
 5. Check the “Expand” option in the “Panel Properties” window and click “Close”.

After moving the panel with window list I had to resize the window list applet (is this really an applet? not sure) manually since it somehow shrinked to zero.

Hope this helps.

BTW, I don't think moving the panels has anything to do with video drivers. What else do you mean by "setting the default monitor"?

PS After playing a bit with panel positions, moved them back to the (smaller) laptop display. Why would I waste any pixel of the (bigger external) primary working display for not-always-needed info?
Hi,

I'm writing for martinmaurer. Thanks for the instructions. They work perfectly fine. Without external monitor, panels show up on laptop display. When external monitor is reconnected, they switch back automatically.

"Setting the default monitor": Means primary monitor - the one who shows the panels and where all new windows pop up. For me, this is the desired setup as I frequently use the panels.

Thx
Andreas

---

