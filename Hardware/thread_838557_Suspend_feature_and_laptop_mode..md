---
title: "Suspend feature and laptop mode."
date: 2008-06-23
forum: Hardware
---

### Post by mempman on 2008-06-23
I have the suspend feature on my laptop (HP dv2000) working fine, regardless of weather I'm running the laptop on AC or battery power.

The problem I have is that if I'm running on AC power and then put the laptop to suspend, and then after the computer has been put into suspend mode, I unplug the AC power cord, and then try to wake the laptop up, the wake procedure fails.  It's almost as if the computer is trying to wake up--the video is powered on but is stuck on a black screen.  

In my /etc/defaults/acpi_support file, I have "enabled_laptop_mode=false;" however, I don't know why yanking the AC cord is failing the wake procedure.


What files should I being to examine to find the solution to this problem?

---

### Post by sdennie on 2008-06-23
That's odd.  One thing you could try would be to hit Ctrl-Alt-F1 and then Ctrl-Alt-F7 to see if that wakes the graphics back up.  You can also look in /var/log/acpid to see if you notice anything.

---

### Post by mempman on 2008-06-23
Ctrl-Alt_F[1-7] don't do squat.
I think what is happening is that my laptop may be going into laptop mode, while the system is in suspend, after the ac cable has been pulled out.

I think the "ENABLE_LAPTOP_MODE=false" option in /etc/defaults/acpi-support is being overlooked?  maybe?

---

### Post by sdennie on 2008-06-23
It's probably not being ignored.  It could be a BIOS problem or a configuration problem.  Unfortunately, I have no idea how to fix the latter with the inclusion of pm-utils in Hardy.

---

