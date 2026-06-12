---
title: "Could Gnome be causing my computer to be unable to shutdown?"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Romanus81 on 2008-01-10
I've always had trouble getting my PC to shutdown fully; I always end up with a screen saying "will now halt" and remaining there until I manually cut the power. I tried adding acpi=on acpi=force, noacpi, everything to grub with no luck, but I did find one thing strange. If I shut down before I log in, that is, I started my computer, and in the log in screen select "shut down", my PC turns off automatically. Secondly, I recently installed PCLinuxOS on my computer, and that fully shuts down. Is it at all possible that it could be something in GNOME that is causing the problem, or is it a general Ubuntu problem?

---

### Post by feistybird on 2008-01-10
remove acpi=xxx 

try add this line into grub :

reboot=b

and / or:

sudo gedit /etc/modules

Add a line:

apm power_off=1

---

