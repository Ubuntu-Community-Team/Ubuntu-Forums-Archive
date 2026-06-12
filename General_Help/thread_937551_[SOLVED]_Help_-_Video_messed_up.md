---
title: "[SOLVED] Help - Video messed up"
date: 2008-10-04
forum: General Help
---

### Post by sagesparrow on 2008-10-04
I am using gutsy on a dell latitude x300 laptop and using an external dell 1704fpt 17" screen.  All was well, but I noticed that some videos I was trying to view looked washed out on Totem, Mplayer, and VLC.  Although the adjustments on VLC could help a little on some videos, it never was right.  But only on some videos.  The same videos on WindowsXP using VLC looked fine.  (i'm dual booting with xp).

I thought I'd fiddle around with the screen and graphics settings.  The laptop has an Intel integrated 855GM video card. I changed the graphics in the settings from Intel Experimental . . . to Intel 810i or something like that just to see if that would fix the problem.  Things got messed up from there.  The external monitor stopped showing anything (it works fine on XP) and I tried adjusting some screen settings in an effort to recover.  Long story short:  Upon booting up the laptop screen doesn't display anything that can be used and the external screen doesn't respond at all.  Some colors and vague patterns are similar to what was there, but only in the top 2/3 of the screen and unusable.  So I can't even get into any configuration settings to try anything more.

Help, what do I do to just get back to where I was when I first started "fixing" things?

---

### Post by sagesparrow on 2008-10-04
bump

---

### Post by iponeverything on 2008-10-04
hiya --

Do <CTL><ALT><F2>

login and run:

sudo dpkg-reconfigure xserver-xorg

---

### Post by sagesparrow on 2008-10-04
I had done that and got:
usr/sbin/dpkg-reconfig: xserver-xorg is not installed

---

### Post by sagesparrow on 2008-10-04
ok, i realize that i had done a slightly different command when i got the above result. (sudo dpkg-reconfigure -phigh xserver-xorg).  Doing the simple dpkg-reconfigure I was able to reconfig xserver and am back up and running.  Thanks.

---

