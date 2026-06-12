---
title: "[SOLVED] Wrong CPU speed listed"
date: 2008-10-26
forum: General Help
---

### Post by xjgnsdof on 2008-10-26
I overclocked my processor (see signature) to 4.01 GHz in the BIOS, but conky lists my processor speed at 3600MHz for each core/CPU. I also get a speed of 3600 MHz when I run cat /proc/cpuinfo.

In gconf-editor, I selected "performance" as my "policy_ac" and "100" as the "performance_ac" value. Is something still scaling my CPU frequency down? I use Ubuntu 8.04 32-bit; could that be the reason that 400 MHz aren't taken into account?

---

### Post by 3rdalbum on 2008-10-26
I believe you need to turn off CPU scaling in your BIOS. I had to.

---

### Post by xjgnsdof on 2008-10-26
I originally tried to do that, but I didn't find the settings for Intel SpeedStep until I consulted my motherboard manual. On my Gigabyte motherboard, "CPU EIST Function" and "CPU Enhanced Halt (C1E)" under Advanced BIOS Options are the settings that govern CPU frequency scaling.

After disabling those, the "performance" power policy that I set earlier finally kicked in, and Conky reads my processor speed as 4005 MHz.

---

