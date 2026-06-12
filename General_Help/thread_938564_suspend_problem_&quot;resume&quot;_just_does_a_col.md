---
title: "suspend problem: &quot;resume&quot; just does a cold boot"
date: 2008-10-05
forum: General Help
---

### Post by Kevinator on 2008-10-05
I haven't been able to get any suspend or hibernate variant to do anything even remotely resembling resuming. No matter what I try, the result of pressing the power button always looks exactly as if the machine was just starting up: BIOS POST, GRUB menu, splash screen, login screen.

I've tried several variations of suspend, including /etc/acpi/sleep.sh, s2disk, pm-suspend, and writing to /sys/power/state. I've tried booting with init=/bin/bash to keep things as simple as possible. Whenever I suspend, the system seems to go into the suspend state (everything turns off and the power LED flashes slowly). But if I press the power button, I just get a normal boot.

I don't even know how to begin debugging this, and I haven't been able to think of decent search terms to google for similar problems. So far I haven't found a single similar case anywhere. It's very frustrating.

Any suggestions?

---

### Post by Kevinator on 2008-10-05
Update: pm-hibernate does actually work when starting from init=/bin/bash. Finally, progress. I'm going to retest all the other forms of hibernate (power-off suspend) to gather more data, then see if I can get suspend-to-ram working by tweaking BIOS settings. If not, I may just move forward with power-off suspend, and try to make it work under normal conditions.

---

### Post by Altay_H on 2008-10-05
Have you tried this one?
```
pmi action suspend
```

If none of the others worked, it probably won't either, but it's worth a try.

---

### Post by MaxIBoy on 2008-10-05
It does sound like a BIOS issue. Do you know what model of motherboard you have?

---

