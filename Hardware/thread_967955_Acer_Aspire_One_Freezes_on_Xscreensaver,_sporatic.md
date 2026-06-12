---
title: "Acer Aspire One Freezes on Xscreensaver, sporatic"
date: 2008-11-02
forum: Hardware
---

### Post by gpenguin on 2008-11-02
I have an Acer Aspire ZG5 and am running Xubuntu.  After some work with other posts, all seems to be working fine.  However, when xscreensaver runs, every now and then, when I hit a key to come back (via the login), the entire system freezes.  *NOTHING* works and I have no choice but to push/hold power to shut down.  This has happened only twice in 1 week on my computer and once on my wife's.  We both have the Acer Aspire.  

My screensaver is set to GLMatrix and hers is set to random.  I used the computer plenty and had the screen saver on lots of time for no more than 30 minutes.  When the system has froze, the screen saver was on for no more than 10 minutes and only froze when a key was pressed to come back.

Ideas????

--GPenguin

---

### Post by gpenguin on 2008-11-03
Just FYI, it happened again this time first time out after a change.  I had all xscreensaver packages installed: xscreensaver, data, data-extras, GL, and GL extras.  After my first post, I attempted removing the "extras" packages since they are not supported by Ubuntu.  This morning I booted, logged in, let it go to screen saver and bang...hit the key to get the login dialog and full computer freeze.

Turns out GLMatrix is still within the supported packages for xscreensaver.  Next, I'm going to unintall the GL packages for xscreensaver and see what happens.

--GPenguin

---

### Post by gpenguin on 2008-11-03
Some more info, I uninstalled 'xscreensaver-GL' and now I found something *real* interesting.

I went into XFCE's screensaver control panel and set it to Random.  When the screensaver launched, I get an error 'GLMatrix' can't be found!!!

Get this, XFCE's config and xscreensaver-demo's config had different settings.  'xscreensaver-demo' was set to one screen saver (GLMatrix) and XFCE was set to random (GLxxxxx's were not even in this list).  So I'm wondering if there are two processes trying to control the screen saver.

Does this light any bulbs for anyone?  Also, does anyone know how to disable one or the other so control is in the hands of only one program?

Thanks.

--GPenguin

---

### Post by gpenguin on 2008-11-03
Found out that XFCE4's screensaver configurator is actually gnome-screensaver-preferences.  However, I am sure I'm not running gnome-screensaver.  So no, there is no conflict between screen saver applications.  I'm going to set xscreensaver to random and see if freezing happens again.

--GPenguin

---

### Post by Yashiro on 2008-11-03
Has it crashed or is the video layer above the login box?

Next time you resume from screensaver and it 'freezes', type your password, blind, and press enter.

---

### Post by gpenguin on 2008-11-03
If it freezes again I'll try, but theory is no, it is dead frozen.  Typically pressing the power button (not holding it) will result in OS detection and proper shutdown of the machine.  When the system freezes, not even that will work.  In fact, caps lock and num lock also don't respond.

I've decided to return the machine anyhow but not for a week or so.  So by all means continue to offer up ideas if anyone has them.

--GPenguin

---

