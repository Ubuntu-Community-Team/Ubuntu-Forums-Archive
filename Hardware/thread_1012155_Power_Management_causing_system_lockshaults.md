---
title: "Power Management causing system locks/haults"
date: 2008-12-15
forum: Hardware
---

### Post by amlucent23 on 2008-12-15
I am using Ubuntu 8.10 on my Dell XPS m1530. Everytime the power situation "changes" (Cord is plugged in or switch to battery) the power icon in the systray disappears and this thing pops up on my screen:

[IMG]http://i233.photobucket.com/albums/ee214/amlucent/Screenshot-3.png[/IMG]

if i go to System > Preferences > Power Management my whole system locks up and I have to hold the power to shut it off.  This just started last night, i dunno if it was an update or what.

---

### Post by cake_or_death on 2008-12-16
Do you have compiz turned on?  Check your visual effects setting under System> Preferences> Appearance.  This was happening on my aspire one until I set my visual effects to Normal.  The box appearing on your screen is probably the brightness display.  If you don't want to use compiz, I would try deselecting "reduce backlight brightness" in the Power Management Preferences.

---

### Post by amlucent23 on 2008-12-16
visual effects are set to none. something is wrong with power manager in the systray (battery indicator program) because even if I dont open up System > Preferences > Power Management and lock the whole system, when i log out or shut down it says it is unable to close that program and I have to force kill it.

---

### Post by cake_or_death on 2008-12-16
> **amlucent23 said:**
> visual effects are set to none. something is wrong with power manager in the systray (battery indicator program) because even if I dont open up System > Preferences > Power Management and lock the whole system, when i log out or shut down it says it is unable to close that program and I have to force kill it.

Setting my visual effects to "normal" solved this problem for me.  The Power Manager has been buggy in intrepid all around.  Recent updates seem to have improved matters on my machines, though.

---

