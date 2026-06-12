---
title: "Display brightness keys only work in console - 11.10 on Macbook Pro 5 4"
date: 2012-03-29
forum: Hardware
---

### Post by streetdaddy on 2012-03-29
Kubuntu 11.10
Macbook Pro 5 4
All latest updates
Mactel PPA

The display brightness/backlight keys ie. F1, F2, aren't working when I'm using the GUI, but they work in the console (after Ctrl+Alt+F1)

The KDE keyboard shortcuts for Monitor Brightness are set to default.  I've tried to set custom shortcuts, but this doesn't help.

I can see pommed is running, but I can't find nvidia-bl-dkms or mbp-nvidia-bl-dkms in the mactel ppa, or any other ppa.

In the console, if I run echo 5 > /sys/class/backlight/apple_backlight/brightness, the brightness changes.  But the same command in the KDE GUI does nothing.

Thanks in advance for any helpful suggestions ;) I've tried to apply some of the notes from [https://help.ubuntu.com/community/MacBookPro5-5/Natty](https://help.ubuntu.com/community/MacBookPro5-5/Natty), but this seems to be the last hurdle... (mic not working, but I'll save that for another day)

---

### Post by Tommy_CZ on 2012-07-19
Hi, have you resolved it? The new Long Term Support Ubuntu 12.04 can help with it.

---

