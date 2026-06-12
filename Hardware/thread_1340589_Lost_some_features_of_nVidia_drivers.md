---
title: "Lost some features of nVidia drivers"
date: 2009-11-28
forum: Hardware
---

### Post by HTML-insane on 2009-11-28
So what I've done is:

Removed nVidia's proprietary drivers and installed the Nouveau drivers instead - reboot;
Found that I couldn't get them to work properly, uninstalled them and re-installed nvidia-common;
Booted up, used Jockey to re-install the latest nVidia drivers for Ubuntu (185) (the same way I did when I first installed ubuntu);
Found that I have completely lost shader support for some reason, and can't play my precious ET:QW.

I've tried everything I can think of, including, out of desperation, purging xorg/all graphical applications and re-installing, re-installing nouveau drivers and then purging them, purging nVidia drivers and re-installing them the way I did above, used Ubuntu's, "Oops something went wrong when trying to start X" dialogue to, "reconfigure X for my hardware" and trying earlier versions of the nVidia driver.

I just can't figure out what the Nouveau driver has done to muck up my laptop so completely...

---

### Post by HTML-insane on 2009-11-29
Bump.

Add to that list: I've tried purging my kernel and re-installing it, as well.

---

