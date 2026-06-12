---
title: "Laptop screen brightness &quot;flickering&quot;"
date: 2010-02-16
forum: Hardware
---

### Post by jrtayloriv on 2010-02-16
I am running Ubuntu 9.10 on a Gateway M-6888u laptop. 

My screen brightness is randomly changing between various levels of brightness and dimness -- sometimes every few seconds, sometimes with minutes in between switches. I am currently on AC power, so I don't see why it should be switching ACPI runlevels. Here is an excerpt from my **pm-powersave.log**:

```

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
success.
/usr/lib/pm-utils/power.d/anacron false: start: Job is already running: anacron
success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.
/usr/lib/pm-utils/power.d/95hdparm-apm false: 
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
success.
/usr/lib/pm-utils/power.d/anacron false: start: Job is already running: anacron
success.
/usr/lib/pm-utils/power.d/laptop-mode false: success.
/usr/lib/pm-utils/power.d/sched-powersave false: **sched policy powersave OFF
success.

```... It just repeats that over and over again. Sorry I can't provide more information, I don't really know where to begin diagnosing the problem.

Thanks,
Jrtayloriv

---

### Post by jrtayloriv on 2010-02-17
bump

---

### Post by jrtayloriv on 2010-02-19
bump bump

---

### Post by mjwood0 on 2010-02-20
I know that MSI Wind netbooks have a similar issue.  My wife's would do this constantly until I upgraded the BIOS.

Perhaps a similar bios upgrade would fix your issue too?

The other though I have is that perhaps there is a BIOS setting for ACPI that isn't set right.  I know I had this problem with an older Dell laptop.  For some reason, there were brightness / dimming setting in the bios and when set, would cause my Linux powersaving to go nuts.

Sorry I couldn't be more help.  Good luck!

---

