---
title: "Laptop shuts down due to ACPI bug"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by molo on 2007-10-01
Hello,

Recently my laptop has begun shutting down because of some "*Critical temperature reached*" message.  This message is bogus, and is a well-known bug, but has never appeared on my laptop until recently.  The changes that could have caused it are either an upgrade to Feisty from Edgy in the last few days, or the fact that I've been messing with the new ATI driver recently.

**My question is:**  other than turning ACPI off using "acpi=off" in the boot line, is there anything I can do to fix this behaviour (perhaps just disable shutting down due to overheating in a configuration file somewhere)?

If I do disable ACPI, can I enable APM somehow to take over the power management?

**Bonus question, unrelated:**  How can I insert a module right before the boot process enters the X windows runlevel (I think it's 5)?  I need to manually insert the *fglrx* module at this point because the usual method is not working for some reason, so where do I put the *insmod* command?  Right now it's in *rc.local*, but that's a bit too late, since GDM fails once, then the module gets inserted, and then GDM is started successfully on the second try.

I'd appreciate it if anyone has any ideas to tell me about this, as I'm trying to keep this installation going until Hardy Heron is released, when I'm planning a complete wipe and reinstall.

Thanks very much,
molo

---

### Post by molo on 2007-10-01
OK, well I've solved the bonus question, so here's the solution in case someone does a search for it.

The problem is that Ubuntu actually uses runlevel 2 for normal X-windows mode, instead of runlevel 5 like basically every other distribution I've heard of.  So, my changes in /etc/rc5.d were having no effect since the 5th runlevel is never really entered (as far as I can tell).

So, to add a script (which can do anything, like adding a kernel module using insmod for example) to be executed before GDM starts, I needed to create a script and then create a symbolic link to it in /etc/rc2.d using the name "Sxxscript_name" where "xx" is a 2 digit number that is lower than the equivalent number for the GDM service.

So, since my GDM was being invoked using the "S13gdm" link, I created a link called "S11insert_fglrx_module" which invokes a script that runs insmod to insert the module.

Just FYI.

---

