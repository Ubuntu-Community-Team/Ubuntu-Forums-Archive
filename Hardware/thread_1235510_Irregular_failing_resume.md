---
title: "Irregular failing resume"
date: 2009-08-09
forum: Hardware
---

### Post by joop! on 2009-08-09
My laptop (with Ubuntu 9.04) sometimes fails to resume from suspend. Sometimes the first time after a fresh boot; sometimes only after 3 or 4 successful suspend-resume cycles.

In the case it fails to resume the laptop powers up, the backlight goes on but nothing else happens. Black screen, and the system is not responding to any key- or mouse input. A hard reboot is necessary then.

After a suspend, the pm-suspend.log looks normal. Going from "Running hooks for suspend" to "Performing suspend", and all the hooks in between. And after that, after a successful resume, the log is also looking normal, going from "Awake" and all the hooks after that.

However, after a failing resume, the (second) resume part in the log is completely missing. Only the (first) suspend part is there, the same as after a successful resume. But it looks like pm-utils is not run at all after powering up.

I tried a lot of things already to figure out where this goes wrong. Installing and using uswsusp, unloading modules before suspend, trying all different options in /etc/default/acpi-support, disabling acpid completely, using a different kernel etcetera. But all the times I got the same pattern: most of the times a successful suspend-resume, sometimes failing.

Somehow it seems to me that the process which is handling suspend, is not triggered at all. But so far I can't figure out how this process is going. Is there anyone who can explain to me what is triggering the resume process? Does anyone have an idea where I can look further to figure out what goes wrong?

---

