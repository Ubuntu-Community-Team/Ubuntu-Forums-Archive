---
title: "Can't come out of hibernation correctly"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by ahallubuntu on 2006-07-25
I just installed Dapper on my Dell E1505 laptop and it works fairly well.  When I first tried to hiberate and resume, everything worked fine.  But now, for some reason, when I hibernate and try to resume, I "lose" not only my saved session (completely) but also my hardware settings.  My screen resolution is wrong and my wireless card is completely unrecognized.  I need to reboot immediately to do anything and then everything works - but of course, that completely defeats the purpose of hibernation...

Is there any way to get a feel for what is actually going on when I am hibernating and restoring?  Any way to control how this is done?

Thanks!

---

### Post by cantormath on 2006-07-25
> **ahallubuntu said:**
> I just installed Dapper on my Dell E1505 laptop and it works fairly well.  When I first tried to hiberate and resume, everything worked fine.  But now, for some reason, when I hibernate and try to resume, I "lose" not only my saved session (completely) but also my hardware settings.  My screen resolution is wrong and my wireless card is completely unrecognized.  I need to reboot immediately to do anything and then everything works - but of course, that completely defeats the purpose of hibernation...

Is there any way to get a feel for what is actually going on when I am hibernating and restoring?  Any way to control how this is done?

Thanks!

Did you do any of the updates?

what kind of computer do you have?

you can look in the logs in /var/logs.

---

### Post by ahallubuntu on 2006-07-25
I have a Dell E1505, which is only 3 months old.

Yes, I've done some updates.  I looked for any that might have helped this problem (acpi) but I don't think I installed anything that might have broken it, not sure!  That's why I'm asking if there's any way to look into the problem.  I looked at /var/messages and didn't see anything obvious...

---

