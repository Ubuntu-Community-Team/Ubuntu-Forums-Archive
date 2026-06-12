---
title: "Resume from suspend stopped working - blank screen and cpu fan running slow"
date: 2011-07-21
forum: Hardware
---

### Post by wild_oscar on 2011-07-21
My desktop has been suspending fine since forever. However, 2 weeks ago it decided to stop resuming from suspend. 

I have been using 10.10 and everything was working.

**The symptoms**
- System suspends ok
- When you turn the pc on again, screen is blank
- Hardware seems to be working (disks, fans, etc). However, cpu fan runs slower than usual
- Only solution is to completely turn off the computer, turn the power unit off and on again, and start up

**What I've tried**
- Changed the cpu fan
- Turned on both monitors (dual display, to check if there was a problem with the monitor)
- Booted up from 10.04 with a disk, to see if it was a problem with the update.


I have no idea what could be wrong. Could it be the power supply unit? No idea why, though, as it seems to be working fine aside from this.


I don't know if it's a hardware or software issue, nor what component it could be related to. Any help appreciated.

I attach the pm-suspend.log and Xorg.0.log files

---

### Post by gnome1919 on 2011-07-21
I had the same problem and could solve It with *uswsusp* package.

Solution post link : [http://ubuntuforums.org/showpost.php?p=11029697&postcount=23](http://ubuntuforums.org/showpost.php?p=11029697&postcount=23)

---

### Post by wild_oscar on 2011-07-25
For reference, I managed to fix the issue by replacing the power unit (PSU). 

I have no idea what the problem might have been - the old PSU was working without a problem before and no issue was detected on normal operation (ie, turning on/off, etc).

---

