---
title: "Unity Crashing on Login"
date: 2014-08-10
forum: Hardware
---

### Post by Prime624 on 2014-08-10
I'm using Ubuntu 14.04 on a Sony Vaio laptop. It has integrated Nvidia graphics on an Intel CPU. I haven't had any serious problems with 14.04 until now.


My Ubuntu installation has been working fine since I upgraded from 13.10 a while ago. I booted it up today and the GUI isn't working properly. It will show the login screen like normal and I'll login (to my root account or guest, doesn't make a difference). Then it goes to the default Ubuntu 14.04 wallpaper. The wallpaper is a little taller than my screen and if I mouse over the bottom or top of the screen, the wallpaper will scroll. There is nothing else on the screen (no tray, launcher, desktop icons, etc.) and right clicking the mouse doesn't do anything. Sometimes, a window (really only the contents of it, there is no border or menu, and it appears in the very top left of the screen) pops up saying "system program problem detected" with the cancel or report problem options. Regardless of which button I click, the "window" closes.

I've been trying to fix it for hours, to no avail. I've tried reinstalling the Nvidia drivers numerous times with different methods. I've tried enabling Unity using CCSM. It appeared like the problem detected dialogue, without a border, and it said Unity was disabled. I enabled it and restarted, but nothing. Then I tried reinstalling Unity and restarting it. Finally I got a message (from "dconf reset -f /org/compiz/") saying "error: Cannot autolaunch D-Bus without X11 $DISPLAY". I tried fixing it but I couldn't figure out how.

The last time I shutdown using "sudo poweroff" I noticed a message on the purple shutdown screen: "Could not acquire the 'org.freedesktop.ModemManager1' service name". My internet's been working fine, so I have no idea what it means.

Does anyone have any idea how to fix this?

EDIT: I'm just going to try to reinstall.

---

