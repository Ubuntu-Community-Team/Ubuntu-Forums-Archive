---
title: "Ubuntu can't power off"
date: 2008-09-06
forum: General Help
---

### Post by dijxtra on 2008-09-06
I have problems wiht powering off the computer. Wen I go Log Off and then Turn off, I have to manually power off the machine. Windows XP power the machine automatically. I googled but found no useful advice. I run kubuntu 8.10. Here is some info that could be useful:

```
petra@slon:~$ uname -a
Linux slon 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

```
petra@slon:~$ dmesg | grep apm
[   38.101746] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.101755] apm: disabled - APM is not SMP safe.
```

dmesg | grep acpi gives me noting.

I turned off splash so this is what last few lines say after Turn off:
* Will now halt
halt: Unable to iterate IDE devices: No such file or directory
[   199.565466] Power down.

I tried appending apm=force to kernel line in grub, but it didn't work.

Any other ideas?

---

### Post by me0wth on 2008-11-12
**dijxtra**, I have the same bug, but already for a long time ago, since I have using ubuntu 7.10...and i think we are using the same version of bios, but different acpi settings:
```
$ dmesg | grep apm
[   33.793438] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.793448] apm: overridden by ACPI.
```

```
$ dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
```

I also tried to turn on "apm=force" fuction in kernel, but it gives me nothing, I every time see that error message about halt. And no one command for shutdown actually doesnt work.


Ps. But once when I needed to fix something in the recovery mode in Ubuntu, the command "sudo shutdown -h now" turned computer off correctly...I already dont know what to think about it :confused:

Ps. Sorry for bad english))

---

