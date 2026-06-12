---
title: "ACPI: resource f71882fg conflicts with ACPI region"
date: 2010-04-16
forum: Hardware
---

### Post by andrewthomas on 2010-04-16
I am having trouble monitoring my sensors on a MSI K9A2-CF mobo.  The f71882fg chip driver will not load with the following message
```
ACPI: resource f71882fg [0x600-0x607] conflicts with ACPI region HMOR [0x605-0x606]
```The module will load if I add
```
acpi_enforce_resources=lax
``` to the kernel line.  
Am I looking for trouble by adding this?
The following got me a bit concerned (from [https://bugzilla.redhat.com/show_bug.cgi?id=494938#c5](https://bugzilla.redhat.com/show_bug.cgi?id=494938#c5))

[B]Banging IO ports of a chip from 2 different drivers, the Linux hwmon driver and the
ACPI code is a *really* bad idea and can cause all sort of issues (including
things like changing CPU / RAM voltage or clock speed).[/B]

---

### Post by Yellow Pasque on 2010-04-16
I wish I could quantify the risk, but all I can give you is my personal experience. I ran that same driver on another MSI K9 board for a while and never noticed issues (the board died, but it was due to a shoddy northbridge heatsink on the IGP). I've also run the it87 sensor driver on my current board for a time before lm-sensors changed to a more conservative policy on this issue.

---

### Post by afrodeity on 2010-11-02
I get this message in my logs

```

 ACPI: resource it87 [io  0x0295-0x0296] conflicts with ACPI region IP__ [??? 0x00000295-0x00000296 flags 0x5f]
Nov  1 19:57:00 afrodeity-desktop kernel: [   23.672836] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

Should I do anything?

---

### Post by Yellow Pasque on 2010-11-02
> With previous kernels hwmon drivers used to drive IO ranges which were potentially used by the ACPI code in your BIOS (which is active not only during but also after boot), we now explicitly check for this and if the ACPI code claims the IO-ports used by the hwmon chip, we no longer allow the hwmon driver to load.

Banging IO-ports of a chip from 2 different drivers, the Linux hwmon driver and the ACPI code is a really bad idea and can cause all sort of issues (including things like changing CPU / RAM voltage or clock speed). So the old behaviour was a really bad idea.

So even though this change in behaviour makes some people unhappy as to old behaviour happened to work without problems in their case (by sheer luck really), this change is really for the best!

If you have an Asus motherboard, chances are good there is an ACPI interface to read your sensors, which is safe, and no more sensors.conf tweaking needed for conversion formulas! Make sure you have the asus_atk0110 driver enabled in your kernel configuration to use this. You will also need lm-sensors version 3.1.0 or later.

If you want to restore the old behaviour (which might be dangerous) add: "acpi_enforce_resources=lax" to the kernel cmdline when booting (or add it in grub.conf to make this permanent). 

[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

---

