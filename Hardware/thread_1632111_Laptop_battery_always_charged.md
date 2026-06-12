---
title: "Laptop battery always charged"
date: 2010-11-27
forum: Hardware
---

### Post by kovshenin on 2010-11-27
I'm running 10.04 on an Acer Aspire 5745G laptop and my battery's always showing that it's charged. I don't have a clue how many hrs or % is remaining and when it's 0 it suddenly turns off without any notifications. This is quite annoying especially since I have to work on my laptop. Would anybody kindly suggest on where to start investigating?

Thanks,
~ K

---

### Post by Fafler on 2010-11-27
The ACPI subsystem. But i don't know where exactly.
Try some console command to read battery status. Or maybe another applet that will work.

---

### Post by kovshenin on 2010-11-27
Here's that I see in battery state via terminal

```
$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV
```

---

### Post by themillak on 2010-11-28
when I was searching around for information about making ubuntu work on my acer 7745g, the way I was told to get the battery to be detected correctly by linux was to upgrade the bios from the windows side.  That did the trick for me.

---

