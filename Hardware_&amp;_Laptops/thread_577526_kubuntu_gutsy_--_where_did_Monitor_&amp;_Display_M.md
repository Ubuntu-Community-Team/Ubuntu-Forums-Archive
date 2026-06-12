---
title: "kubuntu gutsy -- where did Monitor &amp; Display Module go?"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by basd on 2007-10-16
I just ran the normal adept updates to gutsy.  Suddenly my monitor is just a "window" on a great big screen, as the resolution is completely wrong.

When I try to run the monitor & display configuration module, I am told that the module cannot be loaded, possible causes are an orphaned module during the last kde upgrade or old third party modules lying around.

The warning suggests removing the applicable module -- but I don't know what module would be the "monitor & display configuration module."

I see that this has been an occasionally reported bug.  All I know is that it >was< working, I ran an update and now it is >not< working.

Since there was a kernel upgrade from .12 to .14, I also tried running in .12, but it didn't make any difference.

I have no idea how to recover from this problem and the computer is essentially not usable in this mode.

Thx.

---

### Post by basd on 2007-10-16
I reinstalled kdebase and the Monitor & Display module returned.  It had been set to 1600x1200, which exceeds the capacity of my monitor.  I set it back to 1280 x 1040 and everything is okay.

It will be interesting if this also solves the power management issues.  Throughout the Gutsy upgrades I have been getting better & worse power management, depending upon the upgrade.  Sometimes, no screen saver/no monitor off/no suspend (despite the correct settings); in different upgrades, suddenly everything works correctly and I get screensaver/monitor off/suspend as it is supposed to work.

---

