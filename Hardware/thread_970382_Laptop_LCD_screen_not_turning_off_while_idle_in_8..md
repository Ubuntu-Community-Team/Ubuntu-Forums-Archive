---
title: "Laptop LCD screen not turning off while idle in 8.10"
date: 2008-11-04
forum: Hardware
---

### Post by WebDrake on 2008-11-04
Hello all,

Following an upgrade to Intrepid, my laptop (a Lenovo Thinkpad R61) no longer powers down the screen after an idle period.

I have a blank-screen screensaver set to start after 5 minutes and, under Display > Power Control have ticked the 'Enable display power management' box and set all the times (Standby after, suspend after, power down after) to 6 minutes.

The screensaver starts, but the LCD screen never turns off -- the backlight remains permanently on.

The LCD powered off fine under Hardy (8.04) with KDE 3.5 and works fine with the GNOME desktop under Intrepid -- it's only Intrepid's KDE 4 that has this problem.

Is there something I'm missing?  If not I will file a bug on Launchpad ...

Thanks in advance for any advice,

    -- Joe

---

### Post by piemonkey on 2008-11-17
Bump.

I have the same problem, there must be a config file somewhere that I can change, since I can turn the backlight off manually by pressing the relevant function key, but I like to have it turn off when idle, to save power. Does anyone know if there is?

---

### Post by piemonkey on 2008-11-17
Ok... I am stupid... The option for power off under Display > Power Control wasn't to power off the whole laptop... I really should have thought that one through.

> **WebDrake said:**
> set all the times (Standby after, suspend after, power down after) to 6 minutes.


Are you sure that setting them all to 6 mins doesn't confuse it, since it won't know which one to do?

---

### Post by piemonkey on 2008-11-17
I tell a lie, it doesn't turn the backlight off, just cuts the signal off, the backlight stays on... So this has stopped being a need for a configuration option, to being possibly a bug.

Anyone know how to solve this one? (the backlight turned off fine under hardy)

---

### Post by WebDrake on 2009-01-19
It is a bug, identified in both Kubuntu and KDE bugtrackers: [https://bugs.launchpad.net/ubuntu/+bug/293603](https://bugs.launchpad.net/ubuntu/+bug/293603)

There's a workaround described in that bug report.  It's not a matter of changing config files -- the config is correctly set, as you can see by typing xset -q.

Having the values all set the same *shouldn't* make a difference, but in this case it appears to (because of the bug).  See bug report for more.

---

