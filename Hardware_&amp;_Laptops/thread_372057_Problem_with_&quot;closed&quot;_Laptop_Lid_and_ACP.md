---
title: "Problem with &quot;closed&quot; Laptop Lid and ACPI"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by DaVinciXL on 2007-02-27
Hey everyone.

I left-clicked on the battery-icon in the lower right corner and chose "shutdown" as action for when the laptop's lid is closed.

Right after the next reboot a little note in the upper left corner popped up telling me that the laptop's lid is closed (well, it obviously isn't) and that the system is shutting down now.
This happens so fast after loading KDE that it is impossible to left-click on the battery icon again in order to undo the change describe above.

Is there a config file I can change? Right now I'm working with the boot paramter acpi=off - but since all other acpi things work well... I want my ACPI back! :)

I already uninstalled all acpi-packes, rebooted and re-installed them - but the problem persists. So there MUST some config file... but which? And what do I have to change there?

Thanks in advance!

PS: If that should matter: I'm using Feisty Fawn with all the latest packages.

---

### Post by tgalati4 on 2007-02-27
Can you turn off power management in the BIOS?  That might disable power management hardware detection upon bootup so you can get into the system and fix the configuration.

Welcome to the community.

---

### Post by DaVinciXL on 2007-02-28
Well, I am actually using the system right now having Power Management disabled via the kernel boot parameter "acpi=off".

The problem: having ACPI disabled, the nice little battery icon in the lower right corner is gone.

So everything is set up to correct my mistake - I just don't know how.

What program brings up this battery icon? Where is it's config file? Changes to /etc/default/acpi and so on don't seem to work...

---

### Post by glaxier on 2007-03-22
I had the same problem as you are. 

Try to find the file "power-managerrc". It's the config file kde-guidance-powermanager uses to store settings related to power management. In my system, it is located in /home/<my_username>/.kde/share/config/power-managerrc. Look for "laptopLidAction" setting and set it to 0 (do nothing).

Kubuntu Edgy uses kde-guidance-powermanager and is written in python as of this time. It seems that it's UI code is in /usr/share/python-support/kde-guidance/guidance-power-manager.py. A particular line says it uses power-managerrc as its configuration filename.

:guitar:

---

### Post by vange on 2007-04-02
I have the same problem as DaVinciXL. I have set power manager to lock screen on lid close, and it locks my screen right after login.

Do you have any ideas for solving or debugging this problem?

Thx,
René

---

### Post by DaVinciXL on 2007-04-02
Found out about that, too - but somehow forget to share the solution in here... sorry.

Thanks anyways.

---

### Post by falt004 on 2008-07-13
I spoke too soon, also having the same problem and can't fix it (just work around it).

----------

*I had a similar problem, but it just went away after performing the workaround mentioned (change the behaviour from suspend to do nothing). Rebooting, then manually suspending it, waking it up, rebooting. Then finally changing the setting (on lid close) from nothing to suspend.*

---

### Post by vange on 2008-07-14
My problem is solved with Kubuntu 8.04. Suspend now works perfectly well when I close laptop lid; it resumes very fast and even connects to another wifi-network, if I move the laptop to a new location while it is suspended.

---

