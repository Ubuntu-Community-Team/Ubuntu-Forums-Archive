---
title: "Laptop Display Issues (VMWare induced?)"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by casperlingus on 2007-10-31
Specs:
Dell Precision M90 Laptop
Dual Display, Laptop Monitor + Dell 2407 (both 1920x1200, 2407 is rotated).
OS:  Gutsy 7.10 w/ encrypted HDD

This setup has  been working fine in Gutsy for the last week and fine in Feisty for months (with same xorg.conf).  All I can remember doing yesterday was installing a Windows image into VMWare Workstation.  Is it possible that WS messed with display settings?  I don't believe it was VMware, but I can't rule it out.

An GNOME SCREENSHOT of Thunderbird is shown below, and my xorg.conf and Xorg.0.log are linked:
[http://66.16.6.172/img/MessedUpDisplayCensored.png](http://66.16.6.172/img/MessedUpDisplayCensored.png)
[http://66.16.6.172/share/xorg.conf.2monitor](http://66.16.6.172/share/xorg.conf.2monitor)
[http://66.16.6.172/share/Xorg.0.log](http://66.16.6.172/share/Xorg.0.log)

Notice the missing captions from the buttons along the top, and the message lines beyond msg empty but icons still showing.  If I mouse over the buttons or click on messages the text reappears, until the window is redrawn (temp covered by another window, minimized&restored, etc).

This image says a lot about the display issue:  it's not just visual -- the screenshot utility in gnome picked up the deformities too.   Also, if I drag the window onto my other monitor, everything instantly appears normal.  Dragging it back to the laptop monitor, it becomes distorted again.  Rather, it looks like it doesn't finish rendering everything when it's on the laptop monitor and it knows it didn't finish rendering it, but it doesn't fix itself.

Help??

-Casper

---

### Post by casperlingus on 2007-11-01
Btw, I should point out that this is not a Thunderbird issue.  Evolution is also distorted, as well as most windows that pop up on that monitor.  It's clearly a gnome/display issue.  

Perhaps I'll install KDE and see if the problem persists...

Update:  This same problem happens in KDE, so it's clearly an X problem.

---

### Post by casperlingus on 2007-12-24
After endless posts on the nvidia linux forum [http://www.nvnews.net/vbulletin/showthread.php?t=101754](http://www.nvnews.net/vbulletin/showthread.php?t=101754)

This problem has been narrowed down to a faulty/overheating video card.  I contacted IT who contacted Dell, and the card was replaced.  The problem has gone away.

---

