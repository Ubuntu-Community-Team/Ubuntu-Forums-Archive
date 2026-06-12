---
title: "Drastic power management tips?"
date: 2008-06-29
forum: Hardware
---

### Post by *Legion* on 2008-06-29
I have a new AMD ["Puma"-based]("http://ubuntuforums.org/showthread.php?p=5288476") Toshiba laptop. I bought it because of the nice and small form factor.

It's far more powerful than I need in a laptop. What I want to do is maximize battery life.

I'm familiar with lesswatts.org and I'm investigating all of that stuff. I have CPUFreq running successfully (using ondemand), and it clocks my CPU down from 2.0 GHz to 500 MHz most of the time.

I'm looking for all ideas for reducing power usage. I've added an entry to GRUB to pass "nosmp" at boot to disable one of my cores, though I haven't tested yet to see if doing that has a positive impact on battery life.

I'm currently using the "fglrx" ATI driver, though I will be trying the "radeonhd" driver (the one in Hardy is a few versions behind, need to pull down a new one).

Anything I can do to increase battery life, I want to know about (and probably do). Are there any less-than-obvious things to try?

---

### Post by elwin_windleaf on 2008-06-29
Christer Edwards ([http://ubuntu-tutorials.com](http://ubuntu-tutorials.com)) has posted a tutorial on using an app called Powertop ([http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/](http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/)) that supposedly can help you trace down hardware that's eating up your battery.

I haven't used it myself (running a desktop), and it was developed by Intel, but it may work for an AMD chipset as well. Worth a try!

---

