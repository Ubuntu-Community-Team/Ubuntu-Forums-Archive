---
title: "Synaptics touchpad unresponsive after suspend"
date: 2008-11-17
forum: Hardware
---

### Post by ace214 on 2008-11-17
I'm running a Gateway cx2619 laptop, and my touchpad doesn't even show up on "xinput list" after resuming.
Any tips to diagnosing or solving this? I know this is a frequent problem, but I haven't seen any specific topics on Gateways.

---

### Post by mbishof on 2010-01-12
I also have this problem running 9.1 on a gateway cx200x.  Have tried:
1) scripts in /etc/pm/sleep.d 
2) .fdi file in /etc/hal/fdi/policy
3) making a xorg.conf file in /etc/X11 (needed to anyway for my tablet, can make tablet work fine even after suspend, but no love for the touchpad)
4) adding psmouse to the modules section of /etc/default/acpi-support and/or uncommenting DOUBLE_CONSOLE_SWITCH=true in this file
5) adding i8042.reset and other similar commands to my /etc/default/grub file in the variable that is defined as quiet splash (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")

None of these suggested solutions work for me.  There must be a way to do this because my computer correctly configures the touchpad upon startup.  I just need to get it to do the same thing when it wakes from a suspend.  What takes care of configuring my touchpad if it isn't done in my xorg.conf file or in a .fdi file?  Any suggestions?

---

