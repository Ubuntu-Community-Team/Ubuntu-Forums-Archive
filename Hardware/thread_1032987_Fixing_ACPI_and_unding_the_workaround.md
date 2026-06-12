---
title: "Fixing ACPI and unding the workaround"
date: 2009-01-06
forum: Hardware
---

### Post by Johnny K on 2009-01-06
It seems that the [ACPI bug]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") has finally been fixed.

So I have two questions:
[LIST=1]
[*]How could I apply a patch in 8.10?
[*]I originally applied [this workaround]("http://www.overclockingwiki.org/forums/showthread.php?t=1645"), which created (overwrote?) files start.d, suspend.d, and resume.d. Will I need to somehow reverse this workaround?
[/LIST]

---

### Post by Johnny K on 2009-01-15
It seems I was able to update ACPI and undo the workaround. And it seems to be working! My computer has been on for a good while, and the load cycle count has not increased at all.

For reference, here's what I did:
[LIST=1]
[*]Removed the following files: **/etc/acpi/start.d/99-hdd-hdd-spin-fix.sh**, **/etc/acpi/suspend.d/99-hdd-hdd-spin-fix.sh**, and **/etc/acpi/resume.d/99-hdd-hdd-spin-fix.sh**
[*]Enabled backports, updated, and restarted
[/LIST]

---

### Post by cyberlion on 2009-01-18
The problem with de cycle count is solved. But, what the temperature of HD?

---

