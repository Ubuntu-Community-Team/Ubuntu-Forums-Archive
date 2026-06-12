---
title: "Bizarre ACPI issues on HP Pavilion Laptop"
date: 2008-12-07
forum: Hardware
---

### Post by bdoe on 2008-12-07
Quick background: I mainly run on AC power on this six-month-old laptop, but the few times I went on battery power, everything seemed to work as they should, particularly with power management and appropriate icon displays. This was when running Hardy i386. I have upgraded to Intrepid since then.

A few days ago, I had my laptop running on battery power, and ran it down all the way to the point where Gnome power management shut off my computer (I have hibernate disabled because my built-in webcam prevents proper hibernation in Ubuntu). That was all fine; however, this is where the weirdness started.

I took my laptop back down to my usual place, plugged it in, turned it on, and continued using it as I usually do, and the battery charging icon showed up, showing the battery was charging. Everything seemed fine until the battery finished charging.  For the next couple of days, I experienced seemingly-random hard lockups (everything freezes, capslock light flashes). By going into my power management settings and setting the idle time before putting the laptop to sleep to "never" (it was set to one hour for AC, 30 minutes for battery). This cured most of the lockups. However, now I frequently get a battery icon showing a grey (instead of green) battery. Hovering over the icon indicates that the battery has 0.9% charge and will be charged in about two hours; but clicking the icon and selecting the battery properties shows the battery as being fully charged. This usually makes the icon go away after a couple of minutes, only to show back up, completely grey, and showing a 0.9% charge remaining, an hour or so later.

typing 'acpi -a' in terminal shows the proper battery state.

Now, with the same grey icon showing up, I unplugged power. Power management properly went into the battery power profile (screen dimmed, etc.), a popup stating I'm running on battery power appeared... But the battery icon disappeared, and never showed back up!  I then plugged AC power back in, the laptop went back to the AC power profile, 'acpi -a' shows the battery is charging, but the charging icon is gone!

Am I making any sense here?  Can someone help explain what's going on here, and maybe help me fix this?

Thanks in advance

---

### Post by bdoe on 2008-12-10
Just an update: Yesterday, I decided to try something.  I disconnected AC power, waited a few minutes, then put the laptop to sleep (suspend). While sleeping, I plugged AC power back in and then woke the laptop back up. The battery icons are once again doing what they're supposed to be doing, and the random lockups are gone.

Looks like I'm off to Launchpad to file a bug report on this.

---

