---
title: "MSI laptop fails to resume after suspend"
date: 2008-09-13
forum: General Help
---

### Post by Frantic225 on 2008-09-13
Hi guys,

I got a MSI GX600 laptop, I've just installed Hardy on it, everything works great except for resuming after a suspend.

Is there a known fix for this? I haven't been able to find one.

When resuming from a suspend, the system just hangs, capsLock doesn't work which from what I've read means the kernel has hung. The display backlight is not on, which means the display isn't started.

The resume also fails in single-user mode and when running the script from console.

I've tried the pm_trace thing, however I'm not sure it worked, it matches different things and sometimes nothing, plus it's supposed to use the sys clock, however it's not changed.

I've tried disabling the NVidia restricted drivers, same result.

Does any of you know of any fix for this plx?

Thanks.

---

### Post by Frantic225 on 2008-09-13
I've read some more stuff and apparently the pm_trace thing isn't working because it's not supported on the amd64 version. :-z any idas?

---

### Post by Frantic225 on 2008-09-13
bumpBUMPbump, anyone?

The hibernate feature really sux, I might as well switch it off, it will prolly be faster, so.. I need the working suspend on the notebook

---

### Post by Frantic225 on 2008-09-14
:-z

---

### Post by Haiyadragon on 2008-11-01
I have the same problem, also a GX600. Not being able to suspend is a big disadvantage for laptops.

The option does appear in the shut down menu but, because the laptop doesn't wake up from it, forces me to do a hard shutdown.

---

