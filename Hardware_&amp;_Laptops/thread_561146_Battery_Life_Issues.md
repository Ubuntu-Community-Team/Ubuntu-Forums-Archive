---
title: "Battery Life Issues"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by littlepriest01 on 2007-09-27
I have heard other people give rave reviews as to the increased battery-life they are experiencing with ubuntu vs. Windows XP SP2. I have a gateway m285-e and for the last few weeks have been experiencing a greatly decreased battery life. I have an extended battery so it was not uncommon for me to get 3 hours 45 minutes out of a full charge in XP. Now that I have switched (Although it seemed fine at first) I am only getting about 50 minutes. Is there some sort of utility to test the life of the battery? Do you think that this could have to do with Ubuntu's power management. I would hate to have to re-install XP just to test a theory. I have noticed that there were alot of people with gateway tablet's out there trying to get their pen to work, any of you guys had problems with this?

---

### Post by mridkash on 2007-09-27
In terminal try this command, it tells you the info about the battery
```
cat /proc/acpi/battery/BAT0/info
```

You'll see a design capacity value and last full capacity value. See if that makes sense.

If the command doesn't work, the battery number may be different.

open filesystem go to proc>acpi>battery>BAT(*num*)>info
and then paste the path of file in terminal with cat command.

---

### Post by TheCanuck on 2007-09-27
Seems like something might not be allowing the CPU to reach sleep states during idle.  Have you taken a look at powertop to see if it enters C3/C4 sleep?

[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)

That should show the battery usage in watts as well as any processes that might be battery hungry.  Take a look at the C-states / P-states.  During idle you should be in the lowest P-State / C3/C4 sleep.

Sometimes ACPI isn't working properly and the cpu spends 100% time in the C0 state ---100% active which means it sucks down the battery.

---

