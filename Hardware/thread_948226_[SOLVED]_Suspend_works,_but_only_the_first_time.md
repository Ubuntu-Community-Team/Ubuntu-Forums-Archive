---
title: "[SOLVED] Suspend works, but only the first time"
date: 2008-10-15
forum: Hardware
---

### Post by kanterjoe on 2008-10-15
I installed Hardy 8.04 a couple weeks ago on a laptop, but cannot suspend it. it doesnt suspend at all if i use the suspend button (it just locks the screen, makes me re-enter my password). 

So to make it suspend, ive been typing '/etc/acpi/sleep.sh sleep' at the command line, which works the first time. any attempts after that will blank the screen and output someting like 'sdb: assuming drive cache: write through' which is especially odd cuz i dont have an sdb drive (sda is my only drive). 

In the command prompt that i typed that command into the ouput is:

```
ifdown: interface eth16 not configured
ifdown: interface wlan0 not configured
ifdown: interface wmaster0 not configured
Shutting down ALSA...done.
Saving the system clock.
memFunction not supported
Function not supported
Setting the system clock.
Ignoring unknown interface eth16=eth16.
Ignoring unknown interface wmaster0=wmaster0.
Ignoring unknown interface wlan0=wlan0.
Setting up ALSA...done.
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
```

anybody know what could be wrong?

---

