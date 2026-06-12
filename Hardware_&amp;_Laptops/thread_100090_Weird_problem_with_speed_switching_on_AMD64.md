---
title: "Weird problem with speed switching on AMD64"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by imrazor on 2005-12-06
I have a very weird problem on my eMachines M6805 laptop. Like most laptops, the processor works at a variable speed. At a low CPU load, the processor runs at 800MHz then switches to 1800MHz when the CPU load spikes. The problem is that my laptop has developed a tendency to shut down when this transition happens. Under Windows, the fix has been to lock the CPU speed at 1800MHz with a program called Rightmark CPU. Is there a comparable utility I could use under Linux to prevent the laptop from just shutting down? I know the answer is probably no, but I thought I'd check it out before I uninstall Ubuntu.

---

### Post by imrazor on 2005-12-06
Well, I appear to have found my own solution with a little creative searching. Apparently killing powernowd will force the CPU to max speed, but changing the laptop power profiles to "performance" and "powersave" will force the CPU to 1800 MHz and 800 MHz respectively, depending on whether the battery is on or not. Hopefully that will prevent my system from shutting down.

---

### Post by dgbauer on 2005-12-25
[QUOTE=imrazor]Well, I appear to have found my own solution with a little creative searching. Apparently killing powernowd will force the CPU to max speed, but changing the laptop power profiles to "performance" and "powersave" will force the CPU to 1800 MHz and 800 MHz respectively, depending on whether the battery is on or not. Hopefully that will prevent my system from shutting down.[/QUOTE]

Thanks! I just noticed this same problem with my M6805 last night...  Where can I set the 'Performance' and 'PowerSave' options for my laptop in Ubuntu 5.10?

---

