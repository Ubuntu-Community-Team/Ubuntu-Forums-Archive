---
title: "smp kernel heavy network load freeze"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by macmanrh7 on 2007-08-05
Hi, i recently updated my Athlon64 to an athlon64 x2 and switched to an smp kernel. kernel version 2.6.22.1

Since, something (sorry, help my how to be more specific) freezes with the network when under heavy network load.

How can I test for what is happening? I notice a similar bug [https://bugs.launchpad.net/ubuntu/+s....15/+bug/53605](https://bugs.launchpad.net/ubuntu/+s....15/+bug/53605) has been posted, any news on that?

Thanks,
macmanrh7

---

### Post by macmanrh7 on 2007-08-05
have tried with "noapic nolapic": so crash anymore, but also no cpufreq & cool&quiet functionality. so not fixed yet! any ideas, anyone?

---

### Post by macmanrh7 on 2007-08-05
changed BIOS MPS version to 1.1 instead of 1.4 (Abit AV8 ), everything runs smoothly now
so far, so good...

---

### Post by macmanrh7 on 2007-08-07
update: there were still crashes, but installing "irqbalancer" seems to have finally fixed it :)

---

