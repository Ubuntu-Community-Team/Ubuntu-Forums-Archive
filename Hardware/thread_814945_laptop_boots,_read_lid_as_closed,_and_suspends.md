---
title: "laptop boots, read lid as closed, and suspends"
date: 2008-06-01
forum: Hardware
---

### Post by Ba66e77 on 2008-06-01
My laptop has decided, without intervention that I can think of, that it should read it's lid as always being closed.  So when I boot up and log in, it loads up the power manager, displays a message that the lid is closed and suspends.  

Nothing I've been able to do (e.g., passing noacpi and noapm to the kernel at boot) has arrested the process, but I don't think it's a hardware problem because if it was wouldn't the screen never come on?  Also, I can boot into failsafe mode and have command line use all day long without problem.

So anyone know how to change things to prevent this from happening, particularly changes I can make from the command line?  The power settings (i.e., the rule that says to suspend when the lid is closed) have to be stored somewhere.  If I can edit that to keep it from suspending, at least I'd be able to use the box.

Thanks.

Details
kubuntu Hardy
Compaq Presario 2200

---

### Post by sdennie on 2008-06-01
I have no way to try this but, it couldn't hurt to give it a shot:

```

sudo chmod -rx /etc/acpi/lid.sh

```

Reverse it by changing -rx to +rx.

---

### Post by Ba66e77 on 2008-06-01
Thanks, vor, but not joy.  I chmod'ed /etc/acpi/lid.sh and /etc/apm/apmd_proxy, but still get the same results.  

I'm about ready to bag it and reinstall Gutsy.  I never had problems with any of this power management stuff before going to Hardy.

---

### Post by falt004 on 2008-07-13
Having the same problem running Kubuntu Hardy on an HP Pavillion ze4900. It happens whenever X server is restarted... I can work around it by changing the action from suspend to do nothing.

---

