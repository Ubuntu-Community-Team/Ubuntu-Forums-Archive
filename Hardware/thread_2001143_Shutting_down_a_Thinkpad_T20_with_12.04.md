---
title: "Shutting down a Thinkpad T20 with 12.04"
date: 2012-06-10
forum: Hardware
---

### Post by Basilios on 2012-06-10
I installed Lubuntu 12.04 on an old Thinkpad T20 I had around the house. The installation went OK, but I have an odd problem when I shut down the laptop.

When I do so, it freezes and does not properly shut down. When it does, it shows the Lubuntu shutdown screen with the dots  below the name. Three dots are blue and two are white. Maybe it can be a  rough indicator for where it freezes?

This happens when using *sudo shutdown -h now* and also when using the Shutdown item in the menu on the bottom right of the desktop.

What additional information can I provide to figure this out?

---

### Post by gordintoronto on 2012-06-10
This might help:

Add acpi=force in grub with these commands:
gksudo gedit /etc/default/grub
find the line which looks like this:
GRUB_CMDLINE_LINUX=""
Change it to:
GRUB_CMDLINE_LINUX="acpi=force"
save the file and exit, then run:
sudo update-grub
It won't help until after you reboot.

Good luck!

---

### Post by Basilios on 2012-06-11
Yup, it works. A minor problem is that if I hibernate or suspend the machine the wireless connection is lost and cannot be gotten back without restarting, but I'm having plenty of problems with the Wifi - I even started another thread on it.

---

