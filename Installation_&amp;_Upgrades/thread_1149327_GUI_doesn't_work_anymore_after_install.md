---
title: "GUI doesn't work anymore after install"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by shad0w_crash on 2009-05-05
Heey,

After updating Ubuntu to the lastest version by using the update manager Ubuntu doesn't work anymore.

When I boot, i see the normal loading screen. After that I see random collored lines on my screen. At last i got a green line on the top of my screen and some week looking traditional Ubunut collors.

I used to boot from repair instead of normal boot. In the menu i used the fix graphics button but it didn't work. I used the check package options and it runnend perfectly.

At last i used the boot to console with netwerk prompt. That did work. My files where in tact, and i could use the internet (by wget). Does anyone now how I:

1) fix the problem
2) if 1 doesn't work, downgrade to a working version
3) maby install KDE trough console if this is a specifike gnome problem?

---

### Post by Steve Meynell on 2009-05-05
This seems to be a hugely common problem.  I too am having the same issue.

[http://ubuntuforums.org/showthread.php?t=1148567](http://ubuntuforums.org/showthread.php?t=1148567)

From what I have found through reading here, the issue is with the video driver.  If you are able to use the newer driver,Version 9.4, from Ati (if that is the video card you have ) then you should be alright.  If you cannot use that driver you will have to change your video card.  And if, like myself, that is not an option then you will have to revert back to an older version.  I am awaiting confirmation on this from the outside world but that is what I have gathered.

I am hoping beyond hope that in the mean time it will be fixed and a simple apt-get update will fix it all and life will go back to normal.

I don't know exactly how to go back in versions without loosing everything but that's my next bit of research I guess.

Steve

---

### Post by shad0w_crash on 2009-05-05
That's not an option, got an onboard video card :(

---

