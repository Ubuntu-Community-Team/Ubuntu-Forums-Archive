---
title: "A Few Problems..."
date: 2010-04-19
forum: Hardware
---

### Post by emperor886 on 2010-04-19
Hey guys, a few things I need help with on my Koala installation. First off, I am running on my Acer Aspire One ZG5 (AOA150) netbook, however using desktop install so that I can dual-boot with XP.

**Problem 1.** When accessing my Windows workgroup at home, trying to copy files never actually works (from the Windows share to Ubuntu). Part of a file will copy, approximately 100mb, and then a "cannot allocate memory" error shows. The computer I am copying from is running Win7 x64. I found one other instance of this problem on Google, although it remains unanswered.

**Problem 2.** YouTube videos are choppy at best; I need new (better) graphics drivers. I have looked on the aspireoneuser.com forums, to no avail.

**Problem 3.**My power management settings for running on battery power no longer work. Up until two days ago, when I closed the lid, Ubuntu would suspend; now it continues to run normally (not even blanking the screen).

Any help is greatly appreciated! :D

---

### Post by hxcobd on 2010-04-19
> **emperor886 said:**
> 
**Problem 2.** YouTube videos are choppy at best; I need new (better) graphics drivers. I have looked on the aspireoneuser.com forums, to no avail.

**Problem 3.**My power management settings for running on battery power no longer work. Up until two days ago, when I closed the lid, Ubuntu would suspend; now it continues to run normally (not even blanking the screen).

Any help is greatly appreciated! :D

2.) Flash performance on ubuntu is pretty bad in general. This is well-known and well-documented. Video drivers likely won't even completely solve it. The best advice I can give is to uninstall Flash, and reinstall it using the newest release straight from Adobe.

3.) My system likes to either randomly change or disable power management settings as well. I'm assuming you're using the Preferences -> Power Management menu?

You may want to try opening GCONF Editor:

hit Alt + F2, type 'gconf-editor' and hit enter

Then navigate to:

Apps -> Gnome-Power-Manager

And look around in those options. See if they conflict with your Preferences panel setting. Change them in GCONF Editor and see if it helps.

---

### Post by emperor886 on 2010-04-20
Hey there; thanks for the info. I've reinstalled Flash, although it still doesn't work right. Oh well, though. As for the power, all the settings were the same, but after I restarted, it started to suspend upon lid close whilst using battery.

Thanks :)

---

