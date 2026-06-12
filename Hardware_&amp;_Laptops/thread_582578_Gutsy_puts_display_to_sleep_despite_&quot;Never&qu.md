---
title: "Gutsy puts display to sleep despite &quot;Never&quot; setting"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by thoughts on 2007-10-20
I just updated 3 systems from Feisty to Gutsy.  On all of these systems, in the Power Management section, I have "Put display to sleep" set to "Never."  With Feisty, this worked properly: the screensaver came on after a while, and it was displayed indefinitely, because the displays never went to sleep.  But with Gutsy, the screensaver is displayed for only a while, after which the displays all go to sleep.

Is anyone else seeing this problem?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by gigoguy on 2007-10-21
Exact same issue here.  What gives?

---

### Post by WolfManz611 on 2007-10-22
I have the same problem you guys do with the monitor going to sleep despite the setting being set to never in gutsy.

---

### Post by Zyith on 2007-10-22
I'll add myself in as a fourth person having this problem.   All I can really add is that it did not do this before Saturday night.  I must have enabled something in the effects area that kicked this on.

---

### Post by tengil on 2007-11-21
This is really quite annoying. After about 10 minutes my laptop screen goes black and I have to press a key to wake it up. Impossible to watch video. Does anyone know anything more about this bug?

---

### Post by ryanrich on 2007-11-27
I'm having the same problem! It's extremely annoying, as I have to boot into Windoze (*gasp*) to watch any video's...

Any solution yet?

---

### Post by tengil on 2007-11-27
Some more info in hope of someone responding with a solution/suggestion.

My comp: HP Compaq nc8430 laptop
OS: 7.10

$ uname -a
Linux tavla 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

Power Management Preferences set to 'never' for all settings.

---

### Post by tengil on 2007-11-27
Here's my dmesg in case it is of any help.

---

### Post by ryanrich on 2007-11-27
Hmmm, you also have an HP laptop and the same graphics card as me, I'm sure that has something to do with this problem. Either related to HP, or ATI.

---

### Post by flukierdonut on 2007-11-27
Yeah I'm having this problem as well.. very annoying when I try to watch movies. I'm using Gutsy on a HP Pavilion dv8000 with the ATI Radeon Xpress 200M. I really hope someone can figure this out!

---

### Post by ryanrich on 2007-11-28
Ok guys.

This problem is definitely related to DPMS.

For a temporary solution, you can do one of the following two things.

Either comment out Option "DPMS" "true" in xorg.conf, or, if you don't want to completely disable DPMS then add the following to xorg.conf:

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

Here's the link to where I found this info, so will keep an eye on it for any further updates.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969)

---

### Post by ryanrich on 2007-11-29
Ok well, this isn't much of a solution since it stops the screen going off completely. So you can't even enable a screensaver.

The problem seems to lie when xgl - ATI - Compiz are combined. Still working on a proper solution... :(

---

### Post by gmc on 2007-11-29
Not just ATI, we're using a Dell (here at work) with an Intel X3100 chipset and it happens here too. I was having similar problems with my Macbook (also intel chipset) but my last re-install seems to have solved the problem.

Gord

---

### Post by flukierdonut on 2007-12-10
replacing gnome screensaver with xscreensaver fixed the problem for me.

---

### Post by laney on 2007-12-31
> **flukierdonut said:**
> replacing gnome screensaver with xscreensaver fixed the problem for me.

Aha, I'm having this problem too (fglrx+compiz+xgl). Did you have to turn off DPMS or just remove gnome-screensaver? Was it a simple apt-get remove gnome-screensaver && apt-get install xscreensaver?

---

### Post by ryanrich on 2008-01-07
Nope, the whole removing gnome-screensaver and installing xscreensaver isn't working for me... :(

---

### Post by Yellow Pasque on 2008-01-07
For some reason, Gutsy gears its power-managment settings towards laptops.
Try this fix:
[http://ubuntuforums.org/showpost.php?p=4069397&postcount=2](http://ubuntuforums.org/showpost.php?p=4069397&postcount=2)

---

### Post by laney on 2008-01-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/30969](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/30969) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **ryanrich said:**
> Nope, the whole removing gnome-screensaver and installing xscreensaver isn't working for me... :(

No, that didn't work for me either. What *did*, however, was adding this to xorg.conf (slight modification of the above):
```
Section "ServerFlags"
  Option "BlankTime" "0"
  Option "StandbyTime" "0"
  Option "SuspendTime" "0"
  Option "OffTime" "0"
EndSection
```
I also added this to the LP bug. With this, screensavers and normal (g-p-m) power management all work. I guess for some reason (xgl?), some values weren't overridable by g-p-m et al, and this allows them to be. It's a mystery, but one that is, for now, fixed for me.

---

### Post by ryanrich on 2008-01-12
Thanks for the fix guys, just made the changes in gconf and restarted, now for some testing! :)

---

