---
title: "which power management system to use on laptop??"
date: 2010-04-20
forum: Hardware
---

### Post by finite9 on 2010-04-20
Just bought a new laptop and Im trying to figure out which tool is the current "best" one to use for power management on a laptop:

pm-utils seems to be in use in latest Ubuntu 9.10/10.04 but it relies on HAL and HAL is in the process of being removed isn't it???

laptop-mode-tools is available in the repos but seems a bit outdated.  Is this why it's not installed as standard?

If you've got a laptop and want to save most power, do you just stick with the default installation?  Which subsystem handles power management then?  Or do you install custom scripts based on Powertop results or install something from the repos?


EDIT.

Just realised that pm-utils supplies just suspend/resume which works for me, but im after something like laptop-mode-tools that is more up-to-date.  I have seen a thread on the forums about using custom scripts based on Powertop recommendations...Is this the way to go or is there something in the repos that does a good enough job out-of-the-box?

---

### Post by khelben1979 on 2010-04-20
According to [this page]("http://wiki.archlinux.org/index.php/HAL") it seems that [UDEV]("http://en.wikipedia.org/wiki/Udev") will work as an replacement for [HAL]("http://en.wikipedia.org/wiki/HAL_%28software%29").

Maybe the wiki pages can give you something important in this?

---

