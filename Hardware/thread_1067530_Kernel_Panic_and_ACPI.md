---
title: "Kernel Panic and ACPI"
date: 2009-02-11
forum: Hardware
---

### Post by kmac on 2009-02-11
So I originally installed Hardy LTS on my Aspire One ZG5 Netbook. However, after a recent kernel update, I got a bootup kernel panic. After some fishing, I found disabling acpi in the boot line allows my computer to boot (acpi=off).

This was great until I realized (duh?) that I had no power management in my OS. The battery is not recognized whatsoever and I have to manually switch off my netbook after shutdown (I considered writing a script to play a splash at the end of shutdown stating "It is now safe to turn off your computer" :)) 

So I'm wondering if there are any better workarounds for getting around a kernel panic (and I can get more details on the error if needed) or an alternative to using acpi for power management. 

Thanks in advance.

---

### Post by k3rnelmustard on 2009-02-11
Go into the BIOS of your lappy, and see if you can find a setting about disabling APIC checks (not ACPI).  I had this problem at one point and disabling that fixed it.  I'm not sure what problems having that turned off does exactly, but if it works, leave it that way, at least until the kernel/config is fixed.  Check next time ur kernel upgrades.

---

### Post by kmac on 2009-02-11
There are no options pertaining to ACPI at all, sorry. BIOS themselves are actually quite limited. I looked into the upgrade for BIOS and debated flashing, however, the upgrade was only to support options for Vista, and we don't do that here...

---

