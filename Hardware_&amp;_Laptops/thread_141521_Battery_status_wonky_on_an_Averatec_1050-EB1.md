---
title: "Battery status wonky on an Averatec 1050-EB1"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by penvzila on 2006-03-08
I have been getting strange battery messages either saying that my battery is almost empty, or the low batt message will pop up and tell me that I have 100% battery.  Also, the indicator in the menubar seems to alternate between full and empty.  Is there some update I need to do to ACPI settings?

---

### Post by penvzila on 2006-03-08
I've been using it on battery for a while, and it serems to randomly jump from saying 5% to the "correct" percentage.  I use quotes because it seems to be draining a heck of a lot faster than in windows.

---

### Post by gohanUbuntu on 2006-03-08
Have you tried with a different battery? I mean...just to check that is not your battery ;) .

Is only an idea!!!

gohanUbuntu
Mexico.

---

### Post by kickaha on 2006-03-08
penvzila:

I am having the same behaviour on an Averatec 3360. I usually run plugged in to AC, and it randomly catches a battery event, switches the monitor over, and pops up those dialogs. I have found that most of the time, if I unplug the AC for a few seconds and plug it back in, that the monitor will reset to AC eventually.

It doesn't seem to be consistent. I tried to 'tail -f /var/log/acpid' for a while to see what messages are being presented, but I haven't had time to analyse it.

If you are doing any reading on acpi, you may encounter discussions of using a new, model-specific DSDT file. I did that, and it didn't fix the battery meter nonsense. However, my fan tachometer and hibernate on lid-close seem to be working ok. :)

I think it's either spurious acpi events on the hardware, or there's (a) bug(s) in the acpi scripts that cause the battery meter to work incorrectly. I haven't found any complaints in searching the forum, so it may be averatec-specific event production.

I have run my system on battery for a lot longer than the 10-12 minutes it warns me about, so I know _my_ battery is ok.

---

### Post by penvzila on 2006-03-08
It is not the battery, it is the indicator.  I guess it's just not that accurate.  I hope it doesn't decide to shut my computer off becauser it thinks the battery is dead, though.

---

