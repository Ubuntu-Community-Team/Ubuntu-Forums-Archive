---
title: "Geforce 5200. Kernel panic"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by weasel fierce on 2006-03-26
So I installed the Nvidia drivers from the repo, went into the BIOS to disable my integrated intel card (it gives me two options for the graphics, onboard and auto, so I figured auto was the one)

When I exit the BIOS and then boot up, I get the text scrolling just fine, as it boots, but around when it displays the bit about Hotplug subsystems, I get a screenfull of errors, and a "kernel panic - not syncing: Fatal exception in interrupt"

Any ideas, or did I miss something I should have done ? 
I tried following the steps for configuring xorg, from  the howto, on the forums, but that wound up breaking x

---

### Post by weasel fierce on 2006-03-26
Ran the Nvidia installer (from the Nvidia site) as well, and it ran and compiled without a problem, but when I boot up, I get the kernel panic as well

---

### Post by weasel fierce on 2006-03-26
Well, I figured out how to ignore the hotplug part (chmod -x /etc/init.d/hotplug) but that also kills the wireless card and sound.
The machine did boot up at least, though

---

