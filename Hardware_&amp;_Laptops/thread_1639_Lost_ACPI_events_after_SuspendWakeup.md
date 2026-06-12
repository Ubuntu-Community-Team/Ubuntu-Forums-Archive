---
title: "Lost ACPI events after Suspend/Wakeup"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by ecmel on 2004-10-22
Hi,

At last the day comes :) my laptop (Fujitsu Siemens Amilo D) can suspend with echo -n 3 &gt;/proc/acpi/sleep and can also resume without a problem. Congrats to Ubuntu devs and community.

The laptop has a suspend button shortcut (Fn-F2) and I can catch the acpi event Button\Sleep. But, after the laptop suspends and resumes, I can no longer catch Button\Sleep and Button\Power events anymore. The echo method still works, but no events :(

Is there a solution for this, i am very close to a working suspend/resume so I do not want to miss this :)

---

