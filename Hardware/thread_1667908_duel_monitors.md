---
title: "duel monitors"
date: 2011-01-15
forum: Hardware
---

### Post by Juvencio on 2011-01-15
Hi to all.

I'm running ubuntu 10.4.
Nvidia divers working 100%
Duel monitor working 100%

If I move my mouse to the right it appears on the 2nd monitor. Good
If I drag a file or app of any kind it won't appear on the 2nd monitor. Not Good
It seems to be a clone of my desktop and not at the same time.
I think it is an independent desktop.

All I need to do is open a file and move it from one monitor to another.
Any advice?

ps. I don't want to enable Xinerama. Cos my monitors can't use the same restitution.

---

### Post by WiFi Ed on 2011-01-15
Have you enabled "TwinView"?

sudo nvidia-settings

---

### Post by Juvencio on 2011-01-16
Thanks WiFi Ed

"TwinView" dose do what I want but it crops the smaller resolution monitor,
so I lose some of the image.

Is there a way to avoid this, I spent hours looking for answers but no luck.

To give you an idea what I'm trying to do is smiler to what (windows) dose.
All you desktop info is on one screen and you can spool over to the other screen when needed.

One screen has a higher resolution then the other.

I've found many questions on this but now answers.
As far as I can find your monitors have to support the same  resolution.

Is this correct, or is there someone who has done this.

---

### Post by WiFi Ed on 2011-01-16
I found this link, but it involves editing your xorg.conf file by hand.
[http://www.oreillynet.com/linux/blog/2007/02/nvidia_twinview_and_xorgconf.html]("http://www.oreillynet.com/linux/blog/2007/02/nvidia_twinview_and_xorgconf.html")

Warning! Backup your existing xorg.conf file first in case of problems, and only modify your xorg.conf file if you are comfortable restoring your backed up original from a command prompt. Because if it doesn't work correctly, you could be unable to start X and you'd not have a graphical user interface. For me, I usually end up re-installing Ubuntu if I screw this up, but that's because I'm an idiot:D

---

