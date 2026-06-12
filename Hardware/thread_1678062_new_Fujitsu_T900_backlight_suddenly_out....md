---
title: "new Fujitsu T900 backlight suddenly out..."
date: 2011-01-29
forum: Hardware
---

### Post by alexsclewis on 2011-01-29
...after a night of heavy drinking.

There were no signs of inverter degradation previously;  it worked perfectly.  I don't believe any physical harm was done to the laptop during the night, but well, you know.  It was connected to a monitor for most of the night, and I suspect that might be the cause...  Although I'm not sure how.

[LEFT]Right now I'm looking in sys/class/backlight for answers, but nothing I alter seems to have any effect ALTHOUGH sys/class/backlight/acpi_video0/bl_power is set to zero, and when I change it to a one and save it, it says:[INDENT]Could not save the file /sys/class/backlight/acpi_video0/bl_power.
Unexpected error: Error writing to file: Invalid argument
[/INDENT]The WEIRD thing is that if I continue with "Continue without saving" and look again, the file now contains a one.

So yeah.  Any thoughts?

EDIT:  Booting into windows makes no difference.  This does not seem good at all.
[/LEFT]

---

