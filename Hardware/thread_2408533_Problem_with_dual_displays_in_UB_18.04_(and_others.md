---
title: "Problem with dual displays in UB 18.04 (and others)"
date: 2018-12-19
forum: Hardware
---

### Post by cschalk on 2018-12-19
I have a Dell Precision Tower 3620 and two Acer monditors connected via Displayport. When I boot and log in, both monitors work properly. However, if I switch to console mode (ctrl + alt + F#). sometimes the monitors are mirrored, and sometimes the console only displays on my primary monitor. and when switching back to graphical mode, the secondary monitor will stay off. Settings and xrandr both show that both monitors are connected and functioning, and I can move the mouse cursor and applications to the second monitor, but nothing displays.  I have to turn the monitor off and back on again before anything displays.

Also, if I lock my screen and walk away, eventually the monitors will sleep. I think it's ubuntu which is sleeping the displays. When I return, the same thing happens, the primary display wakes and I can log back in, and the secondary display is detected, and I can move the cursor and applications over to it, but I have to power cycle the monitor to get the display to actually show up on the second monitor.

I recently upgraded from 14.04, and this happened very occasionally on 14.04, but it wasn't a repeatable and annoying. Since my upgrade to 18.04, it happens every time the monitor sleeps, or I switch to console mode and back.  I can only get it to come back if I power cycle the monitor. Unplugging and re-plugging in the monitor doesn't bring it back.

Any help would be great. I've already verified the latest Intel Integrated Graphics sky lake drivers are installed.

---

### Post by Autodave on 2018-12-19
What, if any, driver did you install for the Nvidia card?  Where did you get the driver from?  I am seeing that the Quadro K620 is what that machine was built with.  If that is not the card in there, what is?

---

### Post by cschalk on 2018-12-19
The NVidia card must have been removed and I'm using the onboard video. This is my work machine, so I don't know it's complete history. I seem to have resolved the issue by removing the second DisplayPort cable and replacing it with HDMI. Perhaps it's a hardware issue with the second displayport port on the back of the computer.

---

