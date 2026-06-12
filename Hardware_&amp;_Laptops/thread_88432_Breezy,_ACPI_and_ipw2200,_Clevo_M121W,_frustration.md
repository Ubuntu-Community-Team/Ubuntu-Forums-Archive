---
title: "Breezy, ACPI and ipw2200, Clevo M121W, frustration"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by siennalizard on 2005-11-10
Dear fellow Ubuntu-ers,
I've got a Clevo M121W here, with serious power management issues, and a few other things. The power management is the real issue, I think. Any help would be appreciated.

When I start the laptop with ACPI enabled in the kernel, just after the kernel itself loads, I get a "critical temperature reached" error, before any acpi modules are loaded. Sometimes it shuts down at this point. The error cites a temperature that would comfortably smelt aluminium (normally in the 1000's of degrees C). That's only until the ACPI modules load. Then it starts to give sensible (though high) values, like 72 deg. C, and shuts down.

But that's only sometimes. If I get the shutdown message on boot before the ACPI modules are loaded, it doesn't always shut down. If I get one afterwards, it always does.

If the computer successfully boots with ACPI enabled, it's normally fine, but issues with the ipw2200 driver crash the machine eventually, and the ndiswrapper drivers for that card load ok (sometimes), and I can scan access points, but dmesg indicates that the MAC address of the AP could not be loaded, and sure enough, "iwconfig eth1" throws up the card details, but a null AP address. "dhclient eth1" at this point has no success.

I feel like I'm on the cusp of getting this thing to work. It's a great little laptop, but pretty useless without ACPI, as apmd seems to throw segmentation faults when used, and the hotplug loading causes IRQ7 to be unclaimed with APM, delaying startup.

I'm past the point of expecting a quick fix, but I should let you all know what I've tried:

- every combination of acpi=off/on, apm=off/on, acpi_irq_iso=7

I'm loathed to abandon ACPI on it completely, as a good boot results in a fully functioning system: all the /proc/acpi files can be read, cpu throttling works logically, battery indicator is accurate, and standby seems to work, too (bar when the ipw2200 module is reloaded, but that's yet another story).

Sometimes, leaving the computer for a few minutes (5 or 6) results in total freezing, which I'm very used to, now! The only way to restart is to use magic SysRq functions or hold down the on button.

Sorry for the length, but as I think these issues are linked, it seems sensible to give you the whole picture. Many thanks.

Warm regards,
J.

PS
I've taken a look at the critical temperature threshold when the system has been running with acpi normally, to find that it's 100 deg C. The computer shuts down during boot giving values between 48(!) and 5305 deg C. Where does it get those threshold values from at boot time? Can I remove boot time temperature probing, or something (seeing as it gives unreasonable values, anyway)?

Suggestions as to what to try next would be great.
Cheers, guys.
J.

---

### Post by siennalizard on 2006-02-21
Finally solved this problem by recompiling my kernel and leaving out thermal.ko support completely. The rest of the ACPI stuff works acceptably, now, although when coming out of hibernate, I can't get all the juice out of my processor: the frequency never goes over 800MHz, and sometimes the battery indicator on the Gnome panel goes crazy and doesn't match what I get from "acpi -V". Must be hald...

If anyone else has the problems described above, I will certainly help them step by step, because I know how frustrating it can be! Don't hesitate to contact me, and I'll let you know the steps to get out of this mess. And before you look anywhere else, it's not a DSDT problem on this model, as I tried to recompile the DSDT to check it, only to find that there are only 2 small errors (that I'm simply not bright enough to fix).

J.

---

