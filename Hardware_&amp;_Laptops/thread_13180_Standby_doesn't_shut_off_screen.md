---
title: "Standby doesn't shut off screen"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by malmjako on 2005-01-29
How do I put my laptop in standby mode, with the screen off?

When I do ```
echo standby > /sys/power/sleep
``` on my HP Omnibook 6000 with acpi enabled, the computer seems to go into some kind of standby mode, but the screen is still on, in console mode. I would like it if the screen would come off too. Neither of the dpms states seem to "survive", that is, issuing ```
sudo dpms standby && sudo echo standby > /sys/power/state
``` doesn't do the trick; the screen shuts off, but then comes back on again when the laptop goes into standby mode.

It should be doable, though, because the klaptopdaemon does it. When I'm in KDE, i can just close the lid (press and hold down the lid button) and the computer goes into standby mode, with the screen off. (I know it's in standby and not in suspend mode, because it resumes much faster than from suspend.) I can't locate any scripts that klaptopdaemon uses, so I don't know how it does it. Does anybody know how klaptopdaemon solves it?

---

### Post by Yoda_Oz on 2005-01-30
this might seem minor but do you have:

Option "DPMS"

enabled in the screen section of your x config?

---

### Post by malmjako on 2005-01-31
Yep, DPMS is enabled. I have no problems putting the screen to sleep using dpms, but when issuing a standby command, the screen comes on again.

---

### Post by malmjako on 2005-02-03
Is anyone using standby mode successfully?

---

