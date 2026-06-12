---
title: "Add suspend option to KDE logout menu"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by thefirstM on 2008-02-20
I am running Kubuntu Gutsy on a desktop PC.  I have made the Suspend and Hibernate functions work successfully.  However, I cannot get the Suspend option to appear on the KDE logout menu.  Hibernate is there, but not suspend.  (I know the suspend option exists because I have seen it on another Kubuntu komputer, which, quite ironically, had FGLRX and therefore could not do Power Management at all.)  I also know that my computer can successfully suspend and resume, because it does so when I execute the script "sudo /etc/acpi/sleep.sh"  Additionally, I had a question about resuming from suspend.  Back when I used Windows XP (glad those days are over!), when I would put my computer in standby, I could wake it up by clicking the USB mouse or typing on the USB keyboard.  However, this does nothing with the PC running linux.  Does anyone know how to fix either of these problems?

---

### Post by thefirstM on 2008-02-24
Bump

---

### Post by pelle.k on 2008-02-29
You *may* have removed these options as a side effect of "making your system suspend" though...
There are several reasons those buttons doesn not show. "cat /sys/power/state" should show at least "mem" and "disk". "groups" should reveal that you are in the powerdev group. guidance-power-manager *may* have to be running (that app in your tray). pm-utils/powersaved may not be compatible with this kde logout menu hack.
Hard to say really.

However, you should be able to suspend and hibernate the computer by right-clicking the power manager you have in your system tray.

---

### Post by thefirstM on 2008-02-29
As my system is a desktop, not a laptop, it does not have guidance-power-manager running, nor will it start.  My system, because it is slightly older, does not support "mem" and therefore supports only "standby" and "disk."  This is probably why the icon is not appearing.  To get suspend to work using my system, I changed the option in /etc/default/acpi-support to "standby" instead of "mem."  Is there any way I can force the icon to appear despite the fact that my system does not support "mem?"

---

