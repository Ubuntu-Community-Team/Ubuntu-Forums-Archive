---
title: "ubuntu overheating cpu"
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by cr4z3d on 2005-02-28
ok.. after awhile i finally got ubuntu to boot on my laptop.. but i need acpi enabled because it over heats and shuts itself off.. i heard something about apm what is that?

---

### Post by LonelyTraveler on 2005-03-04
[QUOTE=cr4z3d]ok.. after awhile i finally got ubuntu to boot on my laptop.. but i need acpi enabled because it over heats and shuts itself off.. i heard something about apm what is that?[/QUOTE]
 I don't know what apm is, but I'm thinking of switching to linux soon. I also have a laptop witch is why I would like to know what laptop you have?

---

### Post by wulf on 2005-03-04
[QUOTE=LonelyTraveler]I don't know what apm is, but I'm thinking of switching to linux soon. I also have a laptop witch is why I would like to know what laptop you have?[/QUOTE]
 On my laptop (Packard Bell Easynote M5262), it was detected as a laptop during bootup and all the necessary power management tools seem to have been automatically installed. I do keep a task monitor (gkrellm) running on the desktop - every now and then I'll fire up a program that gets carried away and consumes all the processor cycles but when I spot that activity I can call up a terminal and kill off the rogue program, avoiding any overheating.

Wulf

---

### Post by NemoTheLobster on 2005-03-14
I have had all kinds of problems with my laptop overheating, not just in Ubuntu.  It's an athlon XP 1800+.   It even overheats booting to the diagnostic CD that came with it.

To get Ubuntu to run and keep from shutting down, I had to disable powernowd and install cpufreqd instead.  Then in the cpufreqd config, I've forced it to run at 80% when the CPU is heavily used.  It's not as fast as it could be, but at least it doesn't crash all the time.

---

