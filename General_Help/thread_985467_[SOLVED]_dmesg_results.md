---
title: "[SOLVED] dmesg results ?"
date: 2008-11-17
forum: General Help
---

### Post by gettinoriginal on 2008-11-17
I ran a dmesg to try to find booting problems and got the following results, but do not understand them.  Can someone tell me how to fix them, (if they even need fixed).

Driver 'sd' needs updating - please use bus_type methods 

sda:<4>Driver 'sr' needs updating - please use bus_type methods

ACPI Warning (evxface-0145): Could not enable fixed event 3 [20070126]

---

### Post by RobbMeex on 2008-11-28
I need help with this issue too. 

I don't have the acpi warning though.

---

### Post by drs305 on 2008-11-28
This has been reported as a bug in several kernels and apparently still exists even in the jaunty alpha kernel. It is reported to be harmless in the bug report, linked below. I don't know about the ACPI part.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167")

---

### Post by RobbMeex on 2008-11-28
yup thanks, just saw that.

---

### Post by spiderbatdad on 2008-11-28
> **gettinoriginal said:**
> I ran a dmesg to try to find booting problems and got the following results, but do not understand them.  Can someone tell me how to fix them, (if they even need fixed).

Driver 'sd' needs updating - please use bus_type methods 

sda:<4>Driver 'sr' needs updating - please use bus_type methods

ACPI Warning (evxface-0145): Could not enable fixed event 3 [20070126]

Maybe use lapic or pci=routeirq
Hard to say without the whole file...you can write it to a text file```
dmesg > ~/Desktop/dmesg.txt
```then right click the file and select "create an archive." You can upload the archive here, if you want to, with the manage attachment tool below.

---

