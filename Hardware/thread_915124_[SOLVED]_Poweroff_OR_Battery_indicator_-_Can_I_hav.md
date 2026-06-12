---
title: "[SOLVED] Poweroff OR Battery indicator - Can I have BOTH?"
date: 2008-09-09
forum: Hardware
---

### Post by Tomlin on 2008-09-09
I have a Gateway 400VTX. I've installed 8.04 and am GENERALLY happy with it. I'm having a problem.

When I try to shutdown the computer, it reboots and powers back up. I have to shut it down by holding the power button down, and the next time I power up, it sometimes hangs.

If I change the menu.lst file and add acpi=off, it will power off by clicking the "off" button in the top panel, but when I boot back up, there is no "battery indicator".

I've used every combination of:

acpi=on, acpi=off, acpi=force, apm=power_on, apm=power_off

and can't get it to power off AND show me how much battery power I have left.

Is this possible? I have Ubuntu on two desktops and am really comfortable with them. I don't want to have to switch distros, and I REALLY don't want to go back to windoze on the laptop. But, I don't think physically shutting it down is a good idea, and I NEED to know how much power I have remaining?

HELP!!!

---

### Post by Tomlin on 2008-09-10
I can't risk shutting my laptop down manually every time I quit.

Anyone?

---

### Post by Rurounidaisho on 2008-10-31
I know that this particular laptop has ACPI 1.0b and does have problems with shutting down properly. I've had mine for a year or two and have only had off and on success with it. I also currently have Ubuntu 8.04.1 installed on this system. It seems to do a reboot if I attempt to shut it down from within Gnome. However, if I logout, it seems to shut down properly. I'm not sure if this has something to with how the shutdown command is executed from within the login manager. It works for me as a workaround. I just have to logout and then select shutdown. Hope this helps you out a little or at least gives us a greater chance of finding a better solution.

---

