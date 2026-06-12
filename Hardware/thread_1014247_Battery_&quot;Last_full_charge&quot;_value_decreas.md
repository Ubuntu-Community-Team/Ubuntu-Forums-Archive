---
title: "Battery &quot;Last full charge&quot; value decreasing in Thinkpad T42p"
date: 2008-12-17
forum: Hardware
---

### Post by oneafrikan on 2008-12-17
Hey All,

Wonder if anyone could shed some light on this?

Since switching to Ubuntu, I've been through two standard batteries, and am onto another 9 cell extended battery, which is starting to show the same signs as the other two... after no more than 6 weeks of use.  So I'm quite keen to get it sorted before it deteriorates too far, so that I can be as mobile as I'd like to be.

"**Last full charge**" decreasing aside, I should be getting 4+ hours with the extended battery, but if I'm lucky I get 3 to 3.5 hours - which is what I was getting on the 6 cell when my machine was still windoze.

Basically, the "Last full charge" just keeps decreasing, despite my attempts to keep it from doing so (including discharging fully, charging, discharging fully again), or keeping the battery withinn a charged zone...

[B]
Are there specific steps to take?
Are there specific settings that are advised, that are not standard?
Is this normal?
Is there anything I'm missing?  
[/B]

After much reading, these are the best resources I can find:
[http://delicious.com/search?context=userposts&p=battery&lc=1&u=oneafrikan](http://delicious.com/search?context=userposts&p=battery&lc=1&u=oneafrikan)

At the moment, this is what I've got setup:
installed cpufrequtils
installed laptop-mode-tools
installed pm-utils
installed hdparm

running cat /proc/sys/vm/laptop_mode shows a 2

laptop-mode.conf values are:
ENABLE_LAPTOP_MODE_ON_BATTERY=1
ENABLE_LAPTOP_MODE_ON_AC=0
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0

Anything else?

I'm pretty sure most folks get this, I've just got into the habit of checking my battery status 'cos it's decreasing so quickly, so I'm hoping that either someone knows what's up, or there's a few steps to take to stop this!  Stop the insanity! ;-)

Anyways - thanks in advance ;-)

gareth

---

