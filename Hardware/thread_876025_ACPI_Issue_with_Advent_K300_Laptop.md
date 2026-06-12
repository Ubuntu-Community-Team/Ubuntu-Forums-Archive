---
title: "ACPI Issue with Advent K300 Laptop"
date: 2008-07-31
forum: Hardware
---

### Post by madarcher on 2008-07-31
Hi,

I wonder if anyone can help me solve this issue.  I've just recently acquired an Advent K300 laptop (good spec at a decent price).  However, on booting up the system hangs.  The issue appears to ACPI based as the usual trick of passing noapic nolapic acpi=off pnpbios=off apm=off to the kernel allows it to load.  As does using acpi=ht.  However, using acpi=force doesn't work.

So effectively I have a working laptop that runs at full speed (i.e. hot) and that has no power management (no battery status, no temperature sensors etc).  I also have to manually shut the machine down at the end by pressing the power button.

Any ideas greatly received.

John

System info:
2GB Ram
Intel Centrino T2130 Dual core processors
Ubuntu 8.04 running kernel  2.6.24-19-server #1 SMP

---

### Post by madarcher on 2008-07-31
To give a little more information.  When I boot using acpi=off the last lines echoed to the screen before the system hangs are:

```

Marking TSC unstable due to: TSC halt in idle
ACPI: CPU1 (Power states C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU1] (supports 8 throttling states)
ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor device not present
ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor device not present
ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor device not present
ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor device not present
ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor device not present
Time: acpi_pm clocksource has been installed

```

It's very hard to get a complete listing here as the system hangs before I can even start up a terminal.  I hope these lines might give someone a clue.

John

---

### Post by phidia on 2008-07-31
Having just read a few things that reminded me of bios setting and taking a stab at this I wonder if turning off PNP in bios might have an affect on what you're seeing?
That could be way off though, and acpi settings are apparently an arcane art.
One more wild thought-can you update your bios? Don't do that unless your feel comfortable doing it.

---

### Post by madarcher on 2008-08-01
The bios was altered by "DixonsXP" (the reseller) and a lot of options seem to have been locked out.  They say they did this so that their vista recovery media is locked to the machine more easily!  I can't get a more uptodate bios from them and likewise they are unwilling to release the unmodified version of the bios.

I think you are on to something though as I have to pass the pnpbios=off option to the kernel to get it to boot without throwing an error.

Does anyone have any idea on how to unlock a modified bios?  Can this even be done?

JOhn

---

### Post by phidia on 2008-08-01
I'm not sure but unlocking a bios seems much harder than just replacing it.
You might also tell the reseller that a locked bios doesn't work for your use of the computer maybe it's beyond the return for refund stage though?

Check out [this bios site]("http://driveragentplus.com/?r=28&PHPSESSID=e05gufqijg7hm5b9d0aphdaff0") there are others on the web too.

---

### Post by madarcher on 2008-08-03
I'm seriously considering returning this laptop as I've had to re-install the "other" OS on it and it is still VERY noisy.  I've even tried OpenSUSE 11 and Fedora Core 9 on it and get the same problem.  The issue is a BIOS ACPI and 2.6 Kernel issue and not an Ubuntu 8.04 error.

Unfortunately there does not appear to be any BIOS update for it so I have to conclude that THE ADVENT K300 LAPTOP IS LINUX UNFRIENDLY.  Hopefully anyone else bying this laptop to convert it to Linux will see this in advance.

---

