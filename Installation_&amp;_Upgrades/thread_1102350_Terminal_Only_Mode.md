---
title: "Terminal Only Mode"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by RIT_girl on 2009-03-21
I was running eeebuntu standard on an ASUS and changing some graphics settings. I went from no graphics to the middle graphics with the wand in some window. Than suddenly it restarted (not the computer, just my session). So I logged back in and than after the a minute the screen went black with different colored lines, than back to the main log in screen. After a few repeats and restarts, I wasn't making any progress logging into any of the sessions. I finally got it to work in terminal only mode. How do I restore default settings on this so that I can function again? If I can at least save all my desktop items I'd be happy. 

thanks, and obviously I'm a complete noob on this who has horrible luck with computer!

---

### Post by WatchingThePain on 2009-03-21
Type startx at the prompt. Note any error messages.
I type init 5 normally but thats on pclinuxos.
You might be able to reconfigure x server with xconfigurator or something.
I'm a noob though.
I hate it when that happens.

---

### Post by RIT_girl on 2009-03-21
Okay, doing startx I got

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.XO-lock and start again


somehow "Fatal Server Error" doesn't give me warm fuzzies

---

### Post by WatchingThePain on 2009-03-21
sudo dpkg-reconfigure xserver-xorg

Try that typing that.

---

### Post by RIT_girl on 2009-03-21
Nope, unfortunately the same thing happened. I'm not completely sure what is causing the screen to freak out and restart my session. But I can't log in with Xclient script or (failsafe or regular) GNOME...I can only use failsafe terminal

---

### Post by RIT_girl on 2009-03-21
Okay, I checked grub and everything seems to be okay, but at this point I'm almost looking for recovery help so I can do an install. I just want everything off my desktop!

thanks,
Becky

---

### Post by roblubbers on 2009-03-23
Look for an old copy of xorg.conf. You can find it in /etc/X11/ . Try to find a copy (if it exist) which dates before the changes you made. Then just rename the copy to xorg.conf and press alt-ctrl-backspace.

---

