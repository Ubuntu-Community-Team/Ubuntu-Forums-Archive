---
title: "Invisible process causes high CPU load"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by sapincher on 2008-04-13
I am on an Asus F3SV-X1 laptop with a T7300 Core 2 Duo. Ubuntu is working well for me, but there is one large problem I cannot seem to fix. I routinely take my laptop to school, where it cannot charge for eight or nine hours and so needs to have the longest battery life possible. However, sometimes an invisible process starts to take up 50% of available CPU time, or a full 100% of one of the cores, equivalent to an invisible and useless Folding at Home. There is no CPU-intensive process listed, and it seems to do it randomly. The last time it did it (four minutes ago) I switched compiz on using "compiz --replace," which also starts Avant-window-navigator. This process runs for as long as the computer is on, and even through standby and hibernation. The only way I can turn it off is to reboot, which can get really annoying. Powertop says it is taking about ten more watts than usual with this invisible process, and it is noticeably hotter. I have no idea exactly what is causing this, has anyone else had a similar problem?

---

### Post by sapincher on 2008-04-13
Powertop says that out of 223 interrupts, 180 are caused by "Rescheduling Interrupts." The next largest contributors are usb, firewire, and nvidia. Also, restarting GDM through "/etc/init.d/gdm stop, /etc/init.d/gdm start" does nothing to solve my problem.

---

### Post by sapincher on 2008-04-14
Alright, it's doing it again and I didn't even do "compiz --replace." What is going on here?

---

### Post by thekip on 2008-04-14
Are you sure you're running you're task manager as root (some processes are hidden otherwise).

---

### Post by sapincher on 2008-04-15
> **thekip said:**
> Are you sure you're running you're task manager as root (some processes are hidden otherwise).

I ran "gksu gnome-system-monitor," and it does show many more processes, but it doesn't show the one that is messing up everything. "sudo top" doesn't display it either. It is much more prevalent when I am on battery power, which probably means that it stems from an ACPI process or something akin to that. I am running the generic kernel, and this problem has happened since 2.6.24-12.

---

### Post by sapincher on 2008-04-16
I figured out what it was. Apparently powertop has an immense immense bug where it runs a daemon detached from the console, and takes up 50% of the processor while the gnome-system-monitor shows that it only uses about 4% max. Upon killing this process, my problem goes away immediately. Which is a shame, because I really like powertop. I really only used it for measuring the immediate wattage of my computer. Is there a gnome panel applet that does this instead?

---

