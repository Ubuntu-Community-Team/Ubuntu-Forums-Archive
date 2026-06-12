---
title: "Sensitivity of the brightness key on a thinkpad T420s"
date: 2012-05-14
forum: Hardware
---

### Post by fph on 2012-05-14
Greetings.
 On my Thinpad T420s, pressing the brightness up/down key varies the brightness by 20% at each keypress. I find it too sharp, and I would like to make it more granular (increase/decrease by 10% at a time would be perfect, for instance).

Where do I change that? I found out how to adjust the brightness manually using sysfs, but not how to change the callback function for the brightness hotkeys.

Thanks in advance for your help.

(By the way, I am using 11.10 atm but I plan to upgrade to 12.04).

---

### Post by hikkakaru on 2012-09-02
> **fph said:**
> Greetings.
 On my Thinpad T420s, pressing the brightness up/down key varies the brightness by 20% at each keypress. I find it too sharp, and I would like to make it more granular (increase/decrease by 10% at a time would be perfect, for instance).

Where do I change that? I found out how to adjust the brightness manually using sysfs, but not how to change the callback function for the brightness hotkeys.

Thanks in advance for your help.

(By the way, I am using 11.10 atm but I plan to upgrade to 12.04).


Old thread, but I just found a solution to this problem myself.

I had to add the following to /etc/rc.local, at the bottom but above 'exit 0'

> echo -n 0 > /sys/module/video/parameters/brightness_switch_enabledAfterwards I had the same brightness granularity as I do in Windows (15 steps) on my T420s with intel graphics.

This is on 12.04 with GDM and Gnome-Shell. Hope it helps.

---

