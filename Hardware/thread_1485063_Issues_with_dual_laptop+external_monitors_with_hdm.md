---
title: "Issues with dual laptop+external monitors with hdmi cable"
date: 2010-05-16
forum: Hardware
---

### Post by benpbenp on 2010-05-16
Ubuntu 9.04, Dell studio xps 16
I used an external monitor along with my laptop monitor for several months with a VGA cable. There was an issue with the boundary edge of the external monitor (I have it to the right of my laptop screen) not being exactly correct:  (1) about 2 pixels of the image from the laptop are visible on the left edge of the external monitor, and (2)the cursor disappears around 6 or 7 pixels from left edge of external monitor, i.e. before it even reaches the 2 pixels from the laptop image that aren't supposed to be there.

I came to peace with that issue since it didn't bother me too much, but I include it here for completeness.

Then, I switch to using the hdmi connection, because this solves a strobing effect problem I had with solid regions of dark gray. The boundary edge problem is still present.

The real problem is that whenever I reboot, the following occurs:

1) At first, my cursor is restricted to a portion of the laptop monitor. The entire desktop is visible across both screens, but I cannot move my cursor outside of an invisible box with a lower boundary maybe two inches from the bottom of the laptop screen and a right boundary three inches from the right edge of the laptop screen.
2)To fix this, I can drag an icon from the invisible box to outside of the invisible box. The icon will snap back to where it came from, but suddenly now I can move my cursor anywhere across the two screens.
3)All is not fixed yet. If I open a window, I cannot drag the window anywhere I want. There is a new invisible box that prevents me from dragging the window - for example - all the way to the right of the external monitor, even though without dragging a window the cursor is free to move all the way to those outer regions.
4)To fix this state, I open the display preferences program present in the system menu, swap the position of the two monitors, i.e. drag the laptop monitor to the right of the external monitor, click apply, and then revert back to the laptop screen being on the left. At this point all is fixed.

---

