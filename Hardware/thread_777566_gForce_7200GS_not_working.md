---
title: "gForce 7200GS not working"
date: 2008-05-01
forum: Hardware
---

### Post by funkyjansson on 2008-05-01
Hi. Just finished installing a ASUS gForce 7200GS.

It works fine in windows, but when i boot linux (Kubuntu Hardy) I just get i black screen. I runed the "try to fix xorg" in recovery mode and i'd typed dpkg-reconfigure -phigh xserver-xorg but that did not help me.
I also typed envyng -t and selected "Install the nVidia driver"
but that only resolted in som error msg saying it could not download some packages.

I think what messes up my system is that i have compiz running. Forgot to turn it of before I swaped the cards.
Is there a way of turning compiz of thrug the commandline?

Also i noticed that KDE is running even thoug the screen is black.
I can hear the welcome sound KDE is making when its starting up after I enter my password.

Sorry if theres some bad spelling.

---

### Post by funkyjansson on 2008-05-01
Now it works.

Removed the second screen, reset the xorg.conf and installed the nVidia driver and then it all worked.

Except that I can't change the resolution with xrandr -s anymoore. Why?
It says: 
```
micke@micke-desktop:~$ xrandr -s 1280x768
Failed to change the screen configuration!
micke@micke-desktop:~$

```

Realy anoying. Want to be able to do that cous I'm trying to fix up a mediacenter which can be controlled with my Wiimote. Then beeing able to change the resolution from the wiimote is important cous I have a 16:9 TV and a 4:3 screen at my desktop. And the only way I know how to do that is trugh xrandr.

---

### Post by funkyjansson on 2008-05-02
bumpie bumpie

---

