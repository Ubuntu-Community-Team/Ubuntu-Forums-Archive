---
title: "Sensors not working, although sensors-detect found `ITE IT8712F Super IO Sensors'"
date: 2011-01-23
forum: Hardware
---

### Post by Justcameron on 2011-01-23
I suspect I'm having overheating troubles, so am trying to exctract my cpu temp from ubunutu maverick.

installed lm-sensors
sudo sensors-detect finds:
```
Trying family `ITE'...                                      Yes
Found `ITE IT8712F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f

```
and then adds "it87" to /etc/modules

However after a restart sensors still doesn't find anything:

```
$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

Thanks!

---

### Post by Justcameron on 2011-01-23
Found this in dmesg

```
[    9.103307] it87: Found IT8712F chip at 0x290, revision 5
[    9.103323] it87: Beeping is supported
[    9.103450] ACPI: resource it87 [io  0x0295-0x0296] conflicts with ACPI region IP__ [??? 0x00000295-0x00000296 flags 0x5f]
[    9.103456] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.198724] agpgart-intel 0000:00:00.0: Intel 865 Chipset
```

Then from some searching worked out that adding acpi_enforce_resources=lax to the kernel boot options would fix it. There's some bug filed about it which I didn't really understand...

So cpu was running pretty cool at about 35 deg. I installed cpuburn to see if we can get it to overheat.

---

