---
title: "Exactly what suspend does?"
date: 2008-11-20
forum: General Help
---

### Post by srilyk on 2008-11-20
I've searched but haven't found anything specific, only general information like this:
```
@the-lappy:~$ tail /var/log/pm-suspend.log 
===== Thu Nov 20 15:23:21 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Thu Nov 20 15:23:21 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Thu Nov 20 15:23:21 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu Nov 20 15:23:22 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Thu Nov 20 15:23:23 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu Nov 20 15:23:23 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/95anacron =====
===== Thu Nov 20 15:23:23 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu Nov 20 15:23:23 CST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Thu Nov 20 15:23:23 CST 2008: done running suspend hooks.

```

I'm trying to find out exactly what commands suspend runs when it "suspends" and then "wakes up".

I need(want) to know this because I have a wacom tablet and I can "hot plug" it, but I have to hibernate/wake up (or restart x), and if the status light doesn't turn on, lsusb.

If anyone knows what the commands are, that would be awesome! :guitar:

Thanks for any help!

---

