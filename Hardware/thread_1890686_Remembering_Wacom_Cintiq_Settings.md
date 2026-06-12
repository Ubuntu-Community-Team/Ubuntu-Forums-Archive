---
title: "Remembering Wacom Cintiq Settings"
date: 2011-12-04
forum: Hardware
---

### Post by osarusan on 2011-12-04
I'm using a Wacom Cintiq in a dual monitor set up.

Since the gnome Wacom Tablet Settings application can only handle the most basic settings, and can't do anything in the case of a multiple monitor setup, I have to manually run a few xsetwacom commands every time I use my PC to set the tablet up correctly. I have a script that I run on startup the make this easier for me.

But the problem still comes up whenever the screensaver turns on and the displays get put to sleep. Since the Cintiq also connects by USB, when the display turns off the USB also turns off, and when the display wakes back up, the tablet config resets to the default settings (i.e. stretched across both monitors) and I have to run the script again to reset it.

Running the script constantly like this works, but is this really the only way to do this? Is there no way that gnome can remember the settings for my tablet so that every time it turns on or off (or the USB unplugs and plugs back in) it can retain the same dimensions and I don't have to re-run this script?

---

### Post by Favux on 2011-12-04
Hi osarusan,

That's what the gnome-settings-daemon will eventually do.  You could try to update one of the old daemon's, like Cyberfish's, if you know a little C.  That monitors for those sort of changes like the gnome-settings-daemon and automatically runs the script when they happen.

The other way to go at it is to use wdaemon:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wdaemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wdaemon)  After several vigorous discussions about this problem Peter updated wdaemon so folks had something they could use now.

---

### Post by osarusan on 2011-12-04
Hi Favux,

Thanks for your reply! I'm glad to hear it's being worked on. I don't suppose you know of any expected date for this to be added into gnome-settings-daemon? I'll look into wdaemon for now.

---

### Post by Favux on 2011-12-04
I have no idea on a time frame.  I know it's been going slower than Peter would like.  I think most of the planning has been agreed on at this point, so it's now implementation.  What's needed is a couple of Gnome developers to show a little more interest in it and make it a bit higher priority I guess.

---

### Post by osarusan on 2011-12-05
I wish I was able to help develop, but my coding skills are absolutely zero.

My Cintiq/dual monitor setup has been a thorn in my side for years now, with Ubuntu constantly changing the way they manage wacom with almost every release, and now with Gnome 3 adding a whole new set of configuration problems into the mess. Fortunately I'm able to work around these, but I feel bad for folks who don't have even the amateur level of experience that I do with this. You've always been an amazing help, Favux, and I can't thank you enough for everything you've done.

---

### Post by osarusan on 2012-03-30
Well not a miracle, but I just installed 12.04 beta 2, and WOW! my tablet works with dual monitors, out of the box! No configuring needed (to be fair, I had to calibrate it one time). Settings are remembered across sessions, and don't get lost when the tablet is turned on and off!

Finally!! I am soooo happy about this! :D

---

