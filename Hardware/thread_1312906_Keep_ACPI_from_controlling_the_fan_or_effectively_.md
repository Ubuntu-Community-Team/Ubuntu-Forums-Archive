---
title: "Keep ACPI from controlling the fan or effectively heat computer up?"
date: 2009-11-03
forum: Hardware
---

### Post by Ader_ on 2009-11-03
Hi!
Due to a faulty BIOS it seems as if Ubuntu is unable to turn the fan on again after it has once been turned off, leading to the laptop becoming really hot. The fan is turned off when it goes below 50C. If I boot with ACPI=off the fan runs all the time which is fine with me.

I see two solutions to which I need some advice:
1. Since disabling ACPI works that would have been a solution. Unfortunately disabling this has some rather unfortunate side effects. Is it possible to configure ACPI in such a way that it leaves the fan alone, while keeps control of all the other things ACPI usually keeps control of?

2. I could make a cron which whenever it detects the temperature as being quite low starts a process which heats the computer up again and another cron which turns this process off again when the temperature reaches, let's say 65C. In this way, the temperature will never go below 50C. What kind of a thing could such a process do to effectively heat the computer up again?

Thanks for your help!

Rasmus

---

