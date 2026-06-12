---
title: "Sony Vaio see only 2.4GB Memory instead of 4GB"
date: 2008-11-15
forum: Hardware
---

### Post by alekons on 2008-11-15
Hello,

I just get a new Sony Vaio (VGN-FW21Z) whith 4GB memory.
I have install Hardy 8.04 and the problem is that OS see only 2.4GB of memory instead of 4GB.
I search the BIOS and there are no option of "Remapping".
Below is some details:

```
$ uname -a
Linux Drago-Ubuntu 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GN
```

```

$ dmesg | head -15
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009dea5000 (usable)
[    0.000000]  BIOS-e820: 000000009dea5000 - 000000009decc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009decc000 - 000000009dedd000 (reserved)
[    0.000000]  BIOS-e820: 000000009dedd000 - 000000009dede000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009dede000 - 000000009df04000 (reserved)
[    0.000000]  BIOS-e820: 000000009df04000 - 000000009df05000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009df05000 - 000000009df06000 (reserved)
[    0.000000]  BIOS-e820: 000000009df06000 - 000000009df12000 (ACPI data)

```


Any ideas how to fix it?


Thanks a lot
Alexis

---

### Post by Yezinki on 2008-11-15
Contact/PM linux23dragon for assistance.....hes the one who can sort it out.

---

### Post by alekons on 2008-11-16
I will and i will post the solution here ...if any 

Thanks

---

### Post by linux23dragon on 2008-11-17
> **alekons said:**
> Hello,

I just get a new Sony Vaio (VGN-FW21Z) whith 4GB memory.
I have install Hardy 8.04 and the problem is that OS see only 2.4GB of memory instead of 4GB.
I search the BIOS and there are no option of "Remapping".
Below is some details:

```
$ uname -a
Linux Drago-Ubuntu 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GN
```

```

$ dmesg | head -15
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009dea5000 (usable)
[    0.000000]  BIOS-e820: 000000009dea5000 - 000000009decc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009decc000 - 000000009dedd000 (reserved)
[    0.000000]  BIOS-e820: 000000009dedd000 - 000000009dede000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009dede000 - 000000009df04000 (reserved)
[    0.000000]  BIOS-e820: 000000009df04000 - 000000009df05000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009df05000 - 000000009df06000 (reserved)
[    0.000000]  BIOS-e820: 000000009df06000 - 000000009df12000 (ACPI data)

```


Any ideas how to fix it?


Thanks a lot
Alexis



Please install the 64bit version of ubuntu-8.10.

Your 32bit Operating system does not have the addressable range to run 4GB of RAM

---

