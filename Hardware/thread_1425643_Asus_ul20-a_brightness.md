---
title: "Asus ul20-a brightness"
date: 2010-03-09
forum: Hardware
---

### Post by l0m31n on 2010-03-09
doesn't work. hotkeys dont always respond, and when they do the brightness doesn't change. manually setting in power management doesn't work either. I'm running 10.04 alpha now, but it didn't work in 9.10. a fix would be great, but even some cmd line usage would be better, running at 100% brightness kills my battery..

---

### Post by gmc on 2010-06-01
You've probably found the solution by now, but by adding "acpi_backlight=vendor" to the line: GRUB_CMDLINE_LINUX_DEFAULT in your /etc/default/grub and then run an sudo update-grub2 and rebooting will solve the problem.

G

---

### Post by l0m31n on 2010-07-18
<333333 FINALLY!! THANK YOU SO MUCH!!!

srsly i've had this computer 4 months.

---

### Post by marcio123 on 2010-07-23
Works ! :) great

---

