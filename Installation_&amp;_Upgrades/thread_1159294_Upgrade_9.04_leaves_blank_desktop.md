---
title: "Upgrade 9.04 leaves blank desktop"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by hbc9000 on 2009-05-14
I recently upgraded from 8.10 to 9.04.
I left the upgrade to run overnight and when I restarted the system in the monrning I got the login screen, logged in, and was presented with a blank orange desktop.  I can move the cursor, use F keys to get to a terminal but get see no menu bars, status panes, nothing. What can I do to get the desktop back?  If I re-install 9.04 will I loose my data on disk?

---

### Post by Carl Hamlin on 2009-05-14
> **hbc9000 said:**
> I recently upgraded from 8.10 to 9.04.
I left the upgrade to run overnight and when I restarted the system in the monrning I got the login screen, logged in, and was presented with a blank orange desktop.  I can move the cursor, use F keys to get to a terminal but get see no menu bars, status panes, nothing. What can I do to get the desktop back?  If I re-install 9.04 will I loose my data on disk?

I've seen a couple of these posts.

I recommend against *ever* going the dist-upgrade route. Instead, back up your important data, smoke the drive, and install from CD. I've had *much* better luck doing it that way.

---

### Post by whoop on 2009-05-14
> **Carl Hamlin said:**
> I've seen a couple of these posts.

I recommend against *ever* going the dist-upgrade route. Instead, back up your important data, smoke the drive, and install from CD. I've had *much* better luck doing it that way.

I've **never** reinstalled ubuntu, and I think you never should (have to). It would be ridiculous imo to reinstall every 6 months (if you want the latest). I would recommend fresh installs for windows, but not for linux, performance shouldn't drop with usage.
With dist-upgrade I suppose you mean update-manager -d? Cause I dist-upgrade every week.

hbc9000: boot from a livecd and edit your /boot/grub/menu.lst and remove quiet splash from the kernel line. Reboot and see what error it gives when booting.

---

### Post by hbc9000 on 2009-05-14
Thanks.  I will try that when I get back to my system.  I'll post what happens.

---

### Post by cavingman on 2009-05-14
I just ran into this exact same problem. Didnt get any error messages after booting after removing "quiet splash" from the kernal line :(

edit: btw my whole install went fine, it was after updating after the install, installing boxee and my video card driver. assuming something in the normal updates is breaking menu's :\

edit again: scratch all that. long day. the vid drivers made my resolution so ginormus the menu was off of the screen. you can delete this useless post :)

---

### Post by hbc9000 on 2009-05-14
> **cavingman said:**
> I just ran into this exact same problem. Didnt get any error messages after booting after removing "quiet splash" from the kernal line :(

edit: btw my whole install went fine, it was after updating after the install, installing boxee and my video card driver. assuming something in the normal updates is breaking menu's :\

edit again: scratch all that. long day. the vid drivers made my resolution so ginormus the menu was off of the screen. you can delete this useless post :)
OK ... I think I have video resolution issues too.  How did you fix it <feeling stoopid)

---

### Post by cavingman on 2009-05-14
try moving your mouse as far into the upper left corner as you can, and click. if the menu is up there somewhere you should be able to open it. then try and find the system menu (2 over to the right from the first one you tried to open.), go system, preferences, and either display or screen resolution or something like that. then just try changin your resolution to something less.

heres a video on how to do it normally (when you can see the menu's :))
[http://www.youtube.com/watch?v=hZKNGXMSChE](http://www.youtube.com/watch?v=hZKNGXMSChE)

if its not the same problem im having then i dont know :\

---

