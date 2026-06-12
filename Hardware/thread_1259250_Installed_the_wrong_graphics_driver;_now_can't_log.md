---
title: "Installed the wrong graphics driver; now can't log in..."
date: 2009-09-06
forum: Hardware
---

### Post by raminaghrobis on 2009-09-06
Hi, I installed the xorg-driver-fglrx package on my other computer, which I thought was the graphics driver for my video card, but it probably wasn't because I now get a weird screen at login and I can't do anything...
Is there some way I can remove the package in the recovery mode? Or should I do something else?
Incidentally, does anybody know which is the correct driver for an ATI Radeon Xpress 200 graphic card?

---

### Post by squenson on 2009-09-06
If you cannot login in graphical mode, can you login in text mode? Try to press Ctrl-Alt-F2 to get to a console where you will be able to login and perform command line actions, then press Ctrl-Alt-F7 to go back to the graphical mode.

---

### Post by PorkyPie on 2009-09-06
> **raminaghrobis said:**
> Hi, I installed the xorg-driver-fglrx package on my other computer, which I thought was the graphics driver for my video card, but it probably wasn't because I now get a weird screen at login and I can't do anything...
Is there some way I can remove the package in the recovery mode? Or should I do something else?
Incidentally, does anybody know which is the correct driver for an ATI Radeon Xpress 200 graphic card?

hehe, i had the same problem witht he same card!! Anyway, read this [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Do the commands in recovery mode.

By the way, are you using an acer pc?

---

### Post by wojox on 2009-09-06
When in recovery mode reset xorg.conf:

```
dpkg-reconfigure xserver-xorg -phigh
```

Then:

```
reboot
```

---

### Post by raminaghrobis on 2009-09-06
Thanks a lot! It works. But I'm still looking for a driver, does anybody know how to install one (I've got xserver-xorg-video-ati and xserver-xorg-video-radeon installed, but stuff like games still don't run well...)

---

