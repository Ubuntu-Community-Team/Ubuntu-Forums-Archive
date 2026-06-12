---
title: "XP time changes after loading ubuntu"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by sawick61 on 2009-11-12
So, when I boot my ubuntu partition and then restart into my Xp partition, for some reason my XP system clock jumps ahead five hours. If i change it and restart back from XP to XP it stays the same but if i restart back into ubuntu, and then back to xp, its changed again. This makes me wonder what other configs are changed when i run ubuntu. Anyone familiar with this?

---

### Post by pvplahing138 on 2009-11-14
yep same problem to me i have dual booted ubuntu and xp home
and evrytime when i run either ubuntu or xp clock changes
even in ubuntu
so i quess its kinda mess with clock
anyways i think it nothing serious>D:p:p:p

---

### Post by efflandt on 2009-11-14
It has been awhile since I looked into how Linux handles the system clock, but if Linux was the only OS on the system, it would set the BIOS clock/calendar to UTC time and display time based on the set time zone.  But it was also smart enough to recognize that if the BIOS clock was current time set by Windows, it would use that instead.

Do you have time zones set properly in both operating systems?  Do you have both set to update the clock automatically (from ntp servers)?  Then as long as you have an internet connection, they should both display correct current local time even if they do not agree how to set the BIOS clock.

PS: Make sure you set proper time zone from System, Administration, Time and Date.  If you only change the displayed time in your window manager, that may not really change the system time zone (ie, you can display a different time zone than Linux is using).  See if the date command in a terminal shows different time or zone than X.  Also see **man tzselect**.

---

### Post by confused57 on 2009-11-14
See this post:
[http://ubuntuforums.org/showpost.php?p=8103487&postcount=2](http://ubuntuforums.org/showpost.php?p=8103487&postcount=2)

To prevent this in the future, you should set Ubuntu to local time rather than UTC when installing.

---

