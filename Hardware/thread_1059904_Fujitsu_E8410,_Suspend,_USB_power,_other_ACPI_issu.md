---
title: "Fujitsu E8410, Suspend, USB power, other ACPI issues"
date: 2009-02-04
forum: Hardware
---

### Post by epirsch on 2009-02-04
Hi All,

I have Ubuntu installed on a Fujitsu E8410 laptop. I'm using the NVidia non-free drivers (177).

While suspend to memory work, I do have the following issues :
USB does not power down.
When I suspend to RAM, the USB ports still receive power. If I leave my USB harddisk plugged-in, the laptop can't stay in suspended state for more than a few hours.
I've search on the web for a solution to this issue, but did not find any.

LCD brighteness key are not working properly. When I press the keys to dim the LCD screen, I see a little window appearing with the current brightness level (and it's decreasing which each key press), but the screen brightness does not change.

The laptop will also never goto spleep automatically after the configured period of time. I know that the ACPI event must work as if I unplug the power, I see the power icon switch to a battery, I can also see the battery charge level. But if power level goes below the suspend threshold or if I leave it idle for the suspend idle period, nothing happens.

Any idea on how I should solve these issues?

---

