---
title: "power management problem"
date: 2010-12-30
forum: Hardware
---

### Post by linuxonbute on 2010-12-30
Since I upgraded to 10.04 i am finding the power management seems to think my battery drains very quickly.
With the mains charger plugged in I get:

norman@norman-laptop:~$ acpi -i
Battery 0: Unknown, 100%
Battery 0: design capacity 7200 mAh, last full capacity 7200 mAh = 100%

I then unplug it from the mains and this is what happens:

after 10 minutes:
acpi -i
Battery 0: Discharging, 98%, discharging at zero rate - will never fully discharge.
Battery 0: design capacity 7200 mAh, last full capacity 7200 mAh = 100%

after 20 minutes:
acpi -i
Battery 0: Discharging, 7%, discharging at zero rate - will never fully discharge.
Battery 0: design capacity 7200 mAh, last full capacity 7200 mAh = 100%

If I don't plug in the power then a few seconds later it shuts down.

It seems strange that this has only happened since I went from 9.10 to 10.04.

Could it be that the software is reading things incorrectly. Is there some way I can disable 

it to see what happens or are there other tests I could do?

---

