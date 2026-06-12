---
title: "[SOLVED] Ubuntu resets hardware clock to GMT"
date: 2008-07-13
forum: General Help
---

### Post by charonred on 2008-07-13
Another annoying little thing; each time I boot into Win XP after exiting 8.04.1 the time has been reset to GMT - it should be GMT+8 as my local timezone.

In Ubuntu I´ve tried using both timeservers (international and local) and manual, but neither seems to make a difference, when I reboot to XP I have to reset the time in it cause the hardware clock has been changed back to GMT time.

Any ideas on why this is happening and how to fix :confused:

---

### Post by estyles on 2008-07-13
I seem to be having the same problem.  I'm not sure that mine is resetting to GMT (although that would make sense), as the time zone is set at US CDT in both Ubuntu and WinXP, but whenever I reboot to Windows, the time is several hours off.  No idea what's causing it... Anyone?

---

### Post by NilsE on 2008-07-13
Windows is using local time and Ubuntu is using GMT time or something like that so here is how to make them both use local time

Right click clock and select preferences.  Turn off UTC.

If that fails do the following:

In a terminal:

gksudo gedit /etc/default/rcS

Look for  this line:  UTC=yes

Change it to: UTC=no

And save it: Then set the time if it is wrong in the System/Administration/Time and Date 

Then either reboot or do this: 

sudo /etc/init.d/hwclock.sh restart

---

### Post by charonred on 2008-07-13
there is no option for UTC in clock preferences, I´ll try your other method and post back when I reboot XP

thanks

---

### Post by charonred on 2008-07-14
Just got back home, booted into Windows and clock is showing correct time again, many thanks.

---

### Post by NilsE on 2008-07-14
> **charonred said:**
> there is no option for UTC in clock preferences, I´ll try your other method and post back when I reboot XP

thanksHmmmm.  Wonder where that went.  It use to be there and don't remember it going away.  Even when it was there it didn't always change the setting so I guess it was removed.

---

