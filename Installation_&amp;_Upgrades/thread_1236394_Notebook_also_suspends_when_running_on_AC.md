---
title: "Notebook also suspends when running on AC"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by Siúlóir on 2009-08-10
Since the upgrade to Jaunty my T400 Notebook autosuspends even when running on AC (that is, reconnected to AC after running on power cell in the same session for a while) and no keyboard and/or mouse action occurs which happens because I use it via an ssh session from my desktop PC.

The power management settings are as follows:

```
On AC Power
Actions
Put computer to sleep when inactive for: Never
When laptop lid closed: Blank screen
Display
Put display to sleep when inactive for: Never
Set display brightness to: 100%
[ ] Dim display when idle

On Battery Power
Actions
Put computer to sleep when inactive for: 30 minutes
When laptop lid closed: Suspend
When battery power is critically low: Shutdown
Display
Put display to sleep when inactive for: 15 minutes
[X] Reduce backlight brightness
[X] Dim display when idle

General
Actions
When the power button is pressed: Ask me
When the suspend button is pressed: Suspend
Notification Area
[ ] Only display an icon when battery power is critically low
[X] Only display an icon when charging or discharging
[ ] Only display an icon when a battery is present
[ ] Always display an icon
Extras
[X] Use sound to notify in event of an error
[X] Dim display when idle
```

---

### Post by phillw on 2009-08-10
A quick 'work round', unless you really need the function is to alter the 'sleep' in battery to 'Never'

That *should* stop the little critter dozing off on you !!!

Your screen should still dim as before.

Regards,

Phill.

---

### Post by Siúlóir on 2009-08-10
Well, actually I want the machine to doze off while on cell but not to doze off while plugged to the grid. 

That's probably the reason why there are two different tabs in the power management dialog...

Somehow power management didn't notice that I plugged the cable when the power cell was drained.

---

